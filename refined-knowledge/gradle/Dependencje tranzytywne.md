up: [[Dependencje Gradle]]

**Dependencje, które mają swoje dependencje.** A więc na przykład biblioteka, która korzysta z innych bibliotek.

Gradle definiuje [[Zadania Gradle|zadania]] oraz [[Zadania Gradle AGP|zadania AGP]], które pozwalają wylistować hierarchię dependencji:

```bash
./gradlew buildEnvironment # zależności pluginów
./gradlew dependencies # zależności dla projektu Java
./gradlew androidDependencies # zależności dla projektu Android
```

Można wyłączyć te zależności, wówczas biblioteka nie będzie korzystała ze swoich dependencji - wybranych lub wszystkich.

```kotlin
testImplementation(group="junit", name="junit", version="4.13.2") {
	isTransitive = false /* Wyłączenie wszystkich zależności biblioteki */
	exclude(group="<chosen_dependency>", module = "<chosen_dependency>") /* Wyłączenie tylko wybranych */
}
```

Można też wziąć sam plik .jar biblioteki bez żadnych dodatkowych dependencji.

```kotlin
testImplementation("junit:junit:4.13.2@jar")
testImplementation(group="junit", name="junit", version="4.13.2", ext: "jar")
```
