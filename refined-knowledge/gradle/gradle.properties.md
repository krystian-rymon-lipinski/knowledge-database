up: [[060 Gradle MOC]]

**Plik służący do określania ustawień konfiguracyjnych procesu Javy, który będzie użyty do wykonywania *buildu***. Możliwe do ustawienia parametry wylistowane są [tutaj](https://docs.gradle.org/current/userguide/build_environment.html#sec:gradle_configuration_properties).

Ustawienia można ustawiać poprzez:
- parametr `-D` w konsoli
- `gradle.properties` w [[Folder .gradle w lokalizacji domyślnej użytkownika|folderze .gradle w lokalizacji domyślnej użytkownika]]
- `gradle.properties` w folderze projektu (lub projektu nadrzędnego, jeśli to subprojekt)
- `gradle.properties` w folderze instalacyjnym Gradle

Lokalizacje te są posortowane od najważniejszej do najmniej ważnej w przypadku zdefiniowania konkretnego parametru konfiguracji w więcej niż jednym miejscu.

