up: [[060 Gradle MOC]]

**Gradle umożliwia definiowanie właściwości przechowujących wartości na kilka różnych sposobów.**

a) lokalnie w pliku `build.gradle` 
W taki sam sposób, w jaki definiuje się zmienne w kodzie: `val version = "2.6.5"`. Dostępne są wówczas tylko dla modułu, w którym zostały zdefiniowane (jeśli w głównym projekcie, to subprojekty i tak nie mają do niego dostępu).

b) jako własności *extra*
Mają one szerszy zasięg, np. subprojekty/moduły mają do nich dostęp. Są one niczym więcej jak parami klucz-wartość <String, Any?>, które trzeba zrzutować na pożądany typ.

```kotlin
/* build.gradle (project-level) */
val someVersion by extra("X.Y.Z")

/* build.gradle (module-level) */
val aVersion = rootProject.extra["someVersion"] as String
```

c) w pliku [[gradle.properties]]

```kotlin
/* gradle.properties */
testString=someString

/* build.gradle (project/module-level)*/
val testString = project.properties["testString"]
```

d) poprzez konsolę
W pliku `build.gradle` definiuje się nazwy zmiennych, których wartości określa się poprzez konsolę

```kotlin
/* build.gradle (project/module-level) */
val param = project.properties["someParam"]
```

```bash
./gradlew paramTask -PsomeParam=heyyy
```