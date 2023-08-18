up: [[071 GitHub Actions]]
#ci-cd-pipeline 

```yaml
name: Integration Pipeline  
  
on:  
  push:  
    branches: '**'  
  pull_request:  
    branches: 'master'  
  
jobs:  
  integrate:  
    runs-on: macos-latest  
    permissions:  # potrzebne do działania akcji "Publish Test Results"
      contents: read  
      issues: read  
      checks: write  
      pull-requests: write  
  
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
  
      - name: Assemble  
        id: 'assemble'  
        run: ./gradlew assembleDebug  
  
      - name: Unit Tests  
        id: unit_tests  
        run: ./gradlew testDebugUnitTest  
        continue-on-error: true  
  
      - name: Instrumented Tests  
        id: instrumented_tests  
        uses: reactivecircus/android-emulator-runner@v2  
        with:  
          api-level: 26  
          script: ./gradlew connectedDebugAndroidTest  
        continue-on-error: true  
  
      - name: Test Results Upload  
        uses: actions/upload-artifact@v3  
        with:  
          name: test-results  
          path: app/build/**/TEST-*.xml  
  
      - name: Test Results Presentation  
        uses: EnricoMi/publish-unit-test-result-action/composite@v2  
        with:  
          files: app/build/**/TEST-*.xml  
  
      - name: Check for failures  
        if: steps.unit_tests.outcome == 'failure' || steps.instrumented_tests.outcome == 'failure'  
        run: exit 1
```


Dodatkowe akcje użyte przy tworzeniu pipeline'a:
- [checkout](https://github.com/marketplace/actions/checkout)
- [setup-java](https://github.com/marketplace/actions/setup-java-jdk) - ustawienie wersji i dystrybucji Javy
- [android-emulator-runner](https://github.com/marketplace/actions/android-emulator-runner) - postawienie emulatora do odpalenia na nim testów insturmentalnych; instrumented tests mają ten problem, że nie wszystkie VM-y działają sensownie; `ubuntu-latest` nie działał, `macos-latest` wydaje się działać; najlepiej śledzić [innych](https://github.com/ReactiveCircus/android-emulator-runner#who-is-using-android-emulator-runner), którzy już te testy do swojego pipeline'a dodali
- [upload-artifact](https://github.com/marketplace/actions/upload-a-build-artifact) - ściągnięcie z VM plików, np. .apk albo rezultatów testów
- [publish-test-results](https://github.com/marketplace/actions/publish-test-results) - przerobienie raportów testów z .xml na informacje bezpośrednio widoczne w GitHub, łącznie z tym, które testy nie przeszły (jeśli jakiekolwiek)
