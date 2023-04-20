up: [[000 HOME]]
#status/in-progress 
#tech-area/gradle 

**Narzędzie do budowania projektów.**
Definiuje **zadania** *(ang. tasks)*, które wykonują pojedynczą operację na plikach projektowych: kompilację plików źródłowych, uruchamianie testów jednostkowych, generowanie plików wykonywalnych na konkretną platformę, etc. Zadania można łączyć w sekwencje, co pozwala na automatyzację różnych procesów tworzenia oprogramowania.

- [[Gradle wrapper|gradle wrapper]]
- [[Pliki .gradle|pliki .gradle]]

- [[Repozytoria Gradle|repozytoria Gradle]]
- [[Pluginy Gradle|pluginy Gradle]]
- [[Dependencje Gradle|dependencje Gradle]]
- [[Zadania Gradle|zadania Gradle]]

- [[Gradle for Android]]

---
> [!NOTE] Uporządkować to

**Skrypty można pisać w języku Groovy oraz w Kotlinie.**

**Wersja Gradle'a zależy od wersji Kotlina!**
https://kotlinlang.org/docs/gradle-configure-project.html#apply-the-plugin
**Ponadto trzeba zdefiniować wersję [[Android Gradle Plugin]]!**
https://developer.android.com/build/releases/gradle-plugin#updating-gradle

**Zmiana czegokolwiek w którymkolwiek ze skryptów Gradle build lub settings)** wymaga synchronizacji projektu (IDE daje taką opcję gdzieś na pasku).

Android Studio daje możliwość zarządzania wieloma aspektami związanymi z Gradle poprzez podejrzenie w [[struktura projektu|strukurę projektu]].

[[Wybrane dependencje gradle z ich znaczeniami]]