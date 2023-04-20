up: [[Pluginy binarne Gradle]]
X: [[Deklarowanie pluginów Gradle przez 'buildscript']]

**API dostępne od wersji 6.0 Gradle.**

```kotlin 
/* settings.gradle.kts */
pluginManagement { /* Deklaracja najwyższego poziomu */
    repositories {
        google() /* Przykładowe publiczne repozytorium */
    }
}
/* build.gradle (project-level) */
plugins { /* Deklaracja najwyższego poziomu */
	java /* Core plugin, wystarczy podać krótką nazwę. */
	id("com.custom.plugin") version "1.0.0" 
	id("yet-another-plugin") version "2.1.1" apply false
}
```

Domyślne zachowanie bloku `plugins` to natychmiastowe znalezienie i zastosowanie zadeklarowanych pluginów. `apply false` zapobiega temu, dzięki czemu można zastosować plugin tylko w wybranych modułach (w plikach `build.gradle` konkretnych modułów).

```kotlin 
/* build.gradle (module-level) */
plugins { /* Deklaracja najwyższego poziomu */
	id("com.custon.plugin")
}
```

---
https://docs.gradle.org/current/userguide/plugins.html#sec:plugins_block