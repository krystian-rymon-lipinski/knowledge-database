up: [[060 Gradle MOC]]

**Używany do trzymania globalnej konfiguracji narzędzia Gradle na urządzeniu użytkownika.** Ponadto zawiera skrypty inicjalizacyjne, scache'owane wersje gradle, pliki logów oraz wersje Gradle pobrane przez wrapper.

Gradle automatycznie czyści ten folder z nieużywanych wersji, plików, zasobów, etc. Każdy typ pliku ma określony czas (możliwy do skonfigurowania przez użytkownia), po którym - jeśli nie jest używany - zostaje usunięty. Konfigurowalna jest również częstotliwość czyszczenia folderu.

Na Windowsie można go najczęściej znaleźć pod ścieżką: `C:\Users\<user>\.gradle`

---
https://docs.gradle.org/current/userguide/directory_layout.html#dir:gradle_user_home