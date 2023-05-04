up: [[070 Gradle MOC]]

**Jako że narzędzie do budowania zazwyczaj nie posiada swojego UI, logi są jedynym sposobem, by dowiedzieć się co dzieje się z projektem podczas wykonywania *tasków***.

**Poziomy logowania (i parametr do ich ustawienia w konsoli):**
- `ERROR (brak?)`
- `QUIET (-q)` 
- `WARN (-w)`
- `LIFECYCLE (bez parametru - poziom domyślny)`
- `INFO (-i)`
- `DEBUG (-d)`

Można też ustawić poziom logowania w pliku [[gradle.properties]] poprzez:
`org.gradle.logging.level=<log_level>`


Logowanie jest możliwe przez `println` i będzie to zakwalifikowane jako poziom `QUIET`. Można również poprzez `logger.*`, gdzie `*` należy zastąpić poziomem logowania.
Do manipulowania logami można użyć [LoggingManagera](https://docs.gradle.org/current/javadoc/org/gradle/api/logging/LoggingManager.html) lub [własnego Loggera](https://docs.gradle.org/current/userguide/logging.html#sec:changing_what_gradle_logs).

**Poziom `DEBUG` może odkrywać wrażliwe dane bezpieczeństwa!** Nie należy z niego korzystać używając publicznego narzędzia CI/CD.

