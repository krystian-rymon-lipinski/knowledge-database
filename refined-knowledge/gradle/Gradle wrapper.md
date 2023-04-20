up: [[070 Gradle MOC]]
#status/in-progress 
#tech-area/gradle 

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

Fragment `Base` w `distributionBase` i `zipStoreBase` oznacza bazowy folder trzymania wersji Gradle. Fragment `Path` definiuje dokładną ścieżkę. 


**Aby manualnie wygenerować pliki Gradle wrappera trzeba [zainstalować](https://docs.gradle.org/current/userguide/installation.html#installing_manually) bazową wersję Gradle i wykonać z terminala polecenie `gradle wrapper` w pożądanej lokalizacji.**

