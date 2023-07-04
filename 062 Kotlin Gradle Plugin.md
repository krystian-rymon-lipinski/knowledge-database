up: [[000 HOME]]
#status/3-freezer 
#tech-area/kotlin #tech-area/gradle 
#gradle/plugin 

Chyba chodzi o to, żeby móc kompilować kotlinowy kod w Gradle. I ogarniać rozmaite inne taski Kotlinowe w projekcie.

```kotlin
id("org.jetbrains.kotlin.android") version "1.8.0" apply false
```

**Wersja pluginu musi być [kompatybilna z Gradle](https://kotlinlang.org/docs/gradle-configure-project.html#apply-the-plugin)** (i Android Gradle Plugin, jeśli to projekt Androidowy).





---
> [!NOTE] Co właściwie daje KGP?
> Czy chodzi tylko o konfigurację dependencji `kapt`?

Jest jeszcze takie coś:
```kotlin
kapt {  
    correctErrorTypes = true  
}
```
Ale to może mieć związek bardziej z [[063 Kapt Gradle Plugin]]
