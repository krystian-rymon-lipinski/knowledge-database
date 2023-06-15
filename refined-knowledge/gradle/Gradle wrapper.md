up: [[060 Gradle MOC]]

**Umożliwia wykonywanie skryptów Gradle i budowanie jego projektów bez manualnego pobierania plików Gradle na lokalne urządzenie.** W to miejsce wystarczy podać pożądaną wersję tego narzędzia w pliku konfiguracyjnym - jeżeli projekt nie będzie jej posiadał, wrapper ją pobierze. Takie podejście ułatwia aktualizację Gradle (wystarczy ją podmienić w pliku konfiguracyjnym) i pracę grupy na tej samej wersji (poprzez wrzucenie pliku konfiguracyjnego wrappera do repozytorium).

Pliki definiowane przez wrapper:
- gradlew, gradlew.bat - skrypty uruchamiające gradle-wrapper na Linuxie i Windowsie (poprzez odpowiednio: `./gradlew <komenda>`, `gradle.bat <komenda>`); w ten sposób można wykonywać [[Zadania Gradle|zadania Gradle]] z konsoli
- gradle/wrapper/gradle-wrapper.jar - zawiera aktualnie ściągniętą wersję Gradle używaną do budowania projektu (cache)
- gradle/wrapper/gradle-wrapper.properties - plik konfiguracyjny wrappera: to tu podaje się wersję Gradle do ściągnięcia przez wrapper; ponadto definiuje miejsce przechowywania dystrybucji Gradle oraz jej plików ZIP

	```
	distributionBase=GRADLE_USER_HOME
	distributionUrl=https\://services.gradle.org/distributions/gradle-7.5-bin.zip
	distributionPath=wrapper/dists
	zipStorePath=wrapper/dists
	zipStoreBase=GRADLE_USER_HOME
	```

Fragment `Base` w `distributionBase` i `zipStoreBase` oznacza [[Folder .gradle w lokalizacji domyślnej użytkownika|folder .gradle w lokalizacji domyślnej użytkownika]]. Fragment `Path` definiuje dokładną ścieżkę dystrybucji w tymże folderze.
`bin` oznacza dystrybucję Gradle zawierającą tylko pliki wykonywalne (skrypty wrappera, etc.). Alternatywą jest dystrybucja `all`, posiadająca pliki źródłowe, którymi można wówczas manipulować.


**Aby manualnie wygenerować pliki Gradle wrappera trzeba [zainstalować](https://docs.gradle.org/current/userguide/installation.html#installing_manually) bazową wersję Gradle i wykonać z terminala polecenie `gradle wrapper` w pożądanej lokalizacji.**
Aby zaktualizować wersję Gradle w projekcie również dobrze jest to zrobić, zamiast tylko podmieniać `distributionUrl` w pliku. Pozwoli to zaktualizować również pliki skryptowe.

```bash
gradle wrapper --gradle-version X.Y.Z
```

Wrappera można [[Konfigurowanie Gradle wrappera|konfigurować]] na własne potrzeby.

---
https://docs.gradle.org/current/userguide/gradle_wrapper.html

