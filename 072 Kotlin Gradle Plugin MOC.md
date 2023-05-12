up: [[000 HOME]]
#status/freezer 
#tech-area/kotlin #tech-area/gradle 
#gradle/plugin 

```kotlin
id("org.jetbrains.kotlin.android") version "1.8.0" apply false
```

**Wersja pluginu musi być [kompatybilna z Gradle](https://kotlinlang.org/docs/gradle-configure-project.html#apply-the-plugin)** (i Android Gradle Plugin, jeśli to projekt Androidowy).



> [!NOTE] Co właściwie daje KGP?
> Czy chodzi tylko o konfigurację dependencji `kapt`?

Jest jeszcze takie coś:
```kotlin
kapt {  
    correctErrorTypes = true  
}
```
