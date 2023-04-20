up: [[070 Gradle MOC]]

**Lokalizacje, z których Gradle będzie w stanie pobierać wybrane dependencje i pluginy zadeklarowane do użycia w kodzie. Można je definiować zarówno dla całego projektu, jak i dla wybranych modułów.**
Należy osobno definiować repozytoria dla dependencji i dla pluginów.

```kotlin
repositories { ... }
```

Możliwe lokalizacje repozytoriów:
- [[Repozytoria publiczne Gradle|repozytoria publiczne Gradle]]
- [własne repozytorium](https://docs.gradle.org/current/userguide/declaring_repositories.html#sec:declaring_custom_repository) - niepublikowanie go do wspomnianych wyżej publicznych
- ścieżka dostępu do plików trzymanych na lokalnej maszynie (poprzez `flatDir { }`)

Możliwe jest dodanie lokalizacji dla konkretnego repozytorium trzymanego na którymś z publicznych - a nawet dostarczyć dane dostępowe, jeśli ono tego wymaga (bo na przykład może być to repozytorium jakiejś firmy).

```kotlin
repositories {
	mavenCentral() /* Przykładowe repozytorium publiczne */
	maven {
		credentials {
			username = "" /* Dobrze te wrażliwe dane przenieść w inne miejsce */
			password = ""
		}
		url = URI("") /* Adres konkretnego repozytorium Maven */
	}
}
```



