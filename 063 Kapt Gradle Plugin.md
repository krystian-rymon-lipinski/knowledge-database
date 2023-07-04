up: [[000 HOME]]
#status/3-freezer
#tech-area/kotlin #tech-area/gradle
#gradle/plugin

**Dla projektu korzystającego z [[062 Kotlin Gradle Plugin|Kotlin Gradle Plugin]] nie można korzystać z [[Konfiguracje dependencji Gradle|konfiguracji dependencji]] `annotationProcessor`, trzeba ją zastąpić `kapt`, która jest dostępna dzięki opisywanemu właśnie pluginowi.**

```kotlin
id("org.jetbrains.kotlin.kapt") version "1.8.20" apply false
```

Dla niektórych konfiguracji Gradle i AGP występuje problem kompatybilności JVM między taskami, opisany [tutaj](https://stackoverflow.com/questions/76030538/android-agp-8-gradle-8-kotlin-1-8-causes-error-in-kapt). Aby go rozwiązać, należy w `build.gradle` dla modułu wrzucić już po dependencjach takie coś:

```kotlin
tasks.withType<KaptGenerateStubs> {  
    kotlinOptions {  
        jvmTarget = "1.8"  
    }  
}
```

---

**Kapt jest już tylko utrzymywany, nie są do niego dodawane nowe funkcjonalności!**
Nowym świecącym narzędziem są [Kotlin Symbol Processing API](https://kotlinlang.org/docs/ksp-overview.html) (KSP). I podobno jest szybsze od kapta ze dwa razy. Aczkolwiek chyba jeszcze nie wspiera wszystkich bibliotek z annotacjami.

---
https://plugins.gradle.org/plugin/org.jetbrains.kotlin.kapt
https://kotlinlang.org/docs/kapt.html