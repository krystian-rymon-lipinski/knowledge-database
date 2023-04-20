up: [[070 Gradle MOC]]
#status/in-progress 
#tech-area/gradle  

**Pliki, które każdy projekt Gradle musi posiadać. Są używane do skonfigurowania projektu.**

#### `settings.gradle`

**Definiuje strukturę projektu.** Należy w nim zadeklarować wszystkie subprojekty i moduły, które powinny zostać użyte do budowania projektu, relacje między nimi oraz właściwości, które są dla nich wszystkich wspólne.

#### `build.gradle`

**Definiuje zachowania wspólne dla całego projektu**, np. używane repozytoria i pluginy.

```kotlin
allprojects {

}
```

- Dla głównego pliku nazwanego inaczej niż `build.gradle`, trzeba go najpierw ustawić:
```bash
./gradlew -b otherName.gradle
```


#### `gradle.properties`

