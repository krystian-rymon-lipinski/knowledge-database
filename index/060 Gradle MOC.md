up: [[000 HOME]]
#status/3-freezer
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

Gradle musi być kompatybilne z Javą (z JVM?): https://docs.gradle.org/current/userguide/compatibility.html

[[Odpalanie Gradle]]
[[Zarządzanie plikami w Gradle]]
[[Słuchacze Gradle]]

[[Wybrane dependencje gradle z ich znaczeniami]]

**Zmiana czegokolwiek w którymkolwiek ze skryptów Gradle build lub settings)** wymaga synchronizacji projektu (IDE daje taką opcję gdzieś na pasku).

> [!NOTE] Jak wywołać manualnie 'sync project'?
> Które taski wchodzą tam w skład? Coś z buildscriptami pewnie.

---
https://docs.gradle.org/current/userguide/userguide.html
https://docs.gradle.org/current/dsl/