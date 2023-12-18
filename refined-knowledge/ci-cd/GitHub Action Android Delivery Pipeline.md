up: [[071 GitHub Actions]]
X: [[GitHub Actions Android Integration Pipeline]]
#ci-cd-pipeline
#status/0-revision-needed 

```yaml
deliver:
    runs-on: macos-latest
    needs: integrate
    env:
      KEYSTORE_FILENAME: keystore-release.jks

    steps:
      - name: Checkout project sources
        uses: actions/checkout@v3

      - name: Setup Java distribution
        uses: actions/setup-java@v3
        with:
          java-version: '17'
          distribution: 'temurin'

      - name: Add permissions for Gradle
        run: chmod +x gradlew

      - name: Decode keystore
        env:
          KEYSTORE_BASE64: ${{ secrets.KEYSTORE }}
        run: echo $KEYSTORE_BASE64 | base64 --decode > $KEYSTORE_FILENAME

      - name: Retrieve keystore properties
        env:
          KEYSTORE_PASSWORD: ${{ secrets.KEYSTORE_PASSWORD }}
          KEY_ALIAS: ${{ secrets.KEY_ALIAS }}
          KEY_PASSWORD: ${{ secrets.KEY_PASSWORD }}
        #keystoreFile path relative to build.gradle.kts file
        run: |
          echo "keystoreFile=./../$KEYSTORE_FILENAME" > ./keystore.properties 
          echo "keystorePassword=$KEYSTORE_PASSWORD" >> ./keystore.properties
          echo "keyAlias=$KEY_ALIAS" >> ./keystore.properties
          echo "keyPassword=$KEY_PASSWORD" >> ./keystore.properties

      - name: Create bundle
        run: ./gradlew bundleRelease

      - name: Upload bundle as an artifact
        uses: actions/upload-artifact@v3
        with:
          name: release-bundle
          path: app/build/outputs/bundle/release/*.aab
          if-no-files-found: error

      - name: Extract version info
        id: extract_version_info
        run: |
          chmod +r ./app/build.gradle.kts
          echo "VERSION_CODE=$(grep "versionCode" ./app/build.gradle.kts | awk '{print $3}')" >> "$GITHUB_OUTPUT"
          echo "VERSION_NAME=$(grep "versionName" ./app/build.gradle.kts | awk '{gsub("\"", "", $3); print $3}')" >> "$GITHUB_OUTPUT"

      - name: Upload bundle to Google Play Store
        env:
          VERSION_CODE: ${{ steps.extract_version_info.outputs.VERSION_CODE }}
          VERSION_NAME: ${{ steps.extract_version_info.outputs.VERSION_NAME }}
        uses: r0adkll/upload-google-play@v1
        with:
          releaseFiles: app/build/outputs/bundle/release/*.aab
          serviceAccountJsonPlainText: ${{ secrets.DELIVERY_PIPELINE_KEY }}
          packageName: com.krystianrymonlipinski.dicepouch.release
          track: internal
          releaseName: ${{ env.VERSION_CODE }} (${{ env.VERSION_NAME }})
          whatsNewDirectory: ./release-notes/whatsnew
          status: draft
```

Dodatkowe akcje użyte przy tworzeniu pipeline'a:
- [upload-artifact](https://github.com/marketplace/actions/upload-a-build-artifact) - ściągnięcie z VM plików, np. .apk albo rezultatów testów
- [upload-android-release-to-play-store](https://github.com/marketplace/actions/upload-android-release-to-play-store) - wysłanie do konsoli wszystkich informacji potrzebnych do [[Udostępnianie aplikacji w konsoli Google Play|udostępnienia aplikacji]]; wymaga skonfigurowania konta w Google Cloud Console i utworzenia konta usługi

Aby móc automatyzować dystrybucję, należy włączyć [[Google Play Developer API]] oraz utworzyć [[Konto usługi Google|konto usługi]] _(ang. service account)_ w konsoli Google Cloud.
Następnie należy dodać konto usługi w konsoli Play jako powiązane i nadać mu uprawnienia:
- wyświetlanie informacji o aplikacji
- tworzenie, edytowanie i usuwanie wersji roboczych aplikacji
- używanie podpisywania aplikacji Google Play
- tworzenie wersji aplikacji do testów

Wrażliwe dane, takie jak klucz .jks i jego dane dostępowe oraz token do API Google'a, należy trzymać na repozytorium w bezpieczny sposób jako [GitHub secrets](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions). Klucz .jks można zakodować używając base64 i zapisać zawartość pliku jako sekret, a później odkodować go w skrypcie.

```shell
base64 -w 0 keystore.jks > keystore-encoded.base64 #.base64 extension!
```
```yaml
- name: Decode keystore  
  env:  
	KEYSTORE_BASE64: ${{ secrets.KEYSTORE }}  
  run: |  
	echo $KEYSTORE_BASE64 | base64 --decode > $KEYSTORE_FILENAME
```

**UWAGA!!!** Hasła z secrets należy zapisać w zmiennej skryptowej $variable. W innym przypadku znaki specjalne w hasłach (np. $, %, etc.) mogą nie zostać ucieknięte, co w konsekwencji zmieni hasło i uniemożliwi podpisanie paczki! Więcej [tutaj](https://github.com/orgs/community/discussions/61323).

```yaml
- name: Retrieve keystore properties  
  env:  
	KEYSTORE_PASSWORD: ${{ secrets.KEYSTORE_PASSWORD }}  
	KEY_ALIAS: ${{ secrets.KEY_ALIAS }}  
	KEY_PASSWORD: ${{ secrets.KEY_PASSWORD }}  
	#keystoreFile path relative to build.gradle.kts file  
  run: |  
	echo "keystoreFile=./../$KEYSTORE_FILENAME" > ./keystore.properties  
	echo "keystorePassword=$KEYSTORE_PASSWORD" >> ./keystore.properties  
	echo "keyAlias=$KEY_ALIAS" >> ./keystore.properties  
	echo "keyPassword=$KEY_PASSWORD" >> ./keystore.properties
```

Jako że _delivery_ musi korzystać z _integration_, można wyłączyć kroki integracji do osobnego pliku, korzystając z [reużywalnych workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows#calling-a-reusable-workflow) i odróżnić wersję _debug_ od _release_ poprzez flagę [kontekstową](https://docs.github.com/en/actions/learn-github-actions/contexts#github-context), np. `github.ref_name`, sprawdzającą nazwę gałęzi wywołującą skrypt (_ang. triggering workflow_)

---
https://stefma.medium.com/how-to-store-a-android-keystore-safely-on-github-actions-f0cef9413784
https://jaysavsani07.medium.com/flutter-ci-cd-with-github-actions-fastlane-part-1-android-14473438072d