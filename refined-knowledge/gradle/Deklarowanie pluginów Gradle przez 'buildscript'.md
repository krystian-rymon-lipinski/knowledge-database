up: [[Pluginy binarne Gradle]]
X: [[Deklarowanie pluginów Gradle przez `plugins` DSL]]

```kotlin
/* build.gradle (project-level) */
buildscript {  
    repositories {  
        google() /* Przykładowe repozytorium publiczne */
    }  
    dependencies {  
	    /* Ścieżki pluginów na publicznych repozytoriach */
		classpath("com.android.application:com.android.application.gradle.plugin:8.0.0")  
        classpath("com.android.library:com.android.library.gradle.plugin:8.0.0")  
    }  
}
/* build.gradle (project-level lub module-level - w zależności od pożądanego zasięgu pluginu) */
apply(plugin = "com.android.library:com.android.library.gradle.plugin:8.0.0")
```

---
https://docs.gradle.org/current/userguide/plugins.html#sec:applying_plugins_buildscript