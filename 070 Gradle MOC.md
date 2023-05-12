up: [[000 HOME]]
#status/in-progress 
#tech-area/gradle 

**Narzędzie do budowania projektów.**
Definiuje **zadania** *(ang. tasks)*, które wykonują pojedynczą operację na plikach projektowych: kompilację plików źródłowych, uruchamianie testów jednostkowych, generowanie plików wykonywalnych na konkretną platformę, etc. Zadania można łączyć w sekwencje, co pozwala na automatyzację różnych procesów tworzenia oprogramowania.

**Skrypty można pisać w języku Groovy oraz w Kotlinie.**

[[Folder .gradle w lokalizacji domyślnej użytkownika|Folder .gradle w lokalizacji domyślnej użytkownika]]
[[Cykl budowania Gradle]]
[[Logi Gradle]]
[[Wieloprojektowy build]]

###### Pliki projektu Gradle:
- folder .gradle w lokalizacji projektu - trzyma cache wersji Gradle używanej przez projekt
- [[Gradle wrapper|gradle wrapper]]
- [[Pliki .gradle|pliki .gradle]]
- [[gradle.properties]]

###### Koncepty Gradle:
- [[projekty Gradle|projekty]]
- [[Repozytoria Gradle|repozytoria]]
- [[Pluginy Gradle|pluginy]]
- [[Dependencje Gradle|dependencje]]
- [[Zadania Gradle|zadania]]
- [[Właściwości Gradle|właściwości]]



---
> [!NOTE] Uporządkować to

[[Odpalanie Gradle]]
[[Zarządzanie plikami w Gradle]]
[[Słuchacze Gradle]]



**Wersja Gradle'a zależy od wersji Kotlina!**
https://kotlinlang.org/docs/gradle-configure-project.html#apply-the-plugin
https://docs.gradle.org/current/userguide/compatibility.html
**Ponadto trzeba zdefiniować wersję [[071 Android Gradle Plugin MOC]]!**
https://developer.android.com/build/releases/gradle-plugin#updating-gradle

**Zmiana czegokolwiek w którymkolwiek ze skryptów Gradle build lub settings)** wymaga synchronizacji projektu (IDE daje taką opcję gdzieś na pasku).

[[Wybrane dependencje gradle z ich znaczeniami]]


> [!NOTE] Jak wywołać manualnie 'sync project'?
> Które taski wchodzą tam w skład?


---
https://docs.gradle.org/current/userguide/userguide.html
https://docs.gradle.org/current/dsl/