up: [[060 Gradle MOC]]

***Build*, który składa się z projektu głównego (_rootProject)_ i subprojektów, zwnych również modułami.**

**Każdy subprojekt (moduł) musi posiadać swój własny plik `build.gradle`, w którym można go skonfigurować bez zmian dla całego projektu oraz zostać dołączony do projektu w pliku `settings.gradle`.** Ponadto należy przeznaczyć dla niego folder o tej samej nazwie co nazwa subprojektu.

```kotlin
/* settings.gradle */
include(":app") /* Dołączenie do projektu subprojektu o nazwie "app" */
```

```kotlin
allprojects { } /* Główny projekt i subprojekty */
subprojects { } /* Tylko subprojekty */
rootProject.version /* Tylko główny projekt */
```

Takie podejście powoduje modularyzację i sprawia, że można wykonywać taski na konkretnych modułach, bez budowania całego projektu za każdą drobną zmianą w którymś z jego subprojektów. 