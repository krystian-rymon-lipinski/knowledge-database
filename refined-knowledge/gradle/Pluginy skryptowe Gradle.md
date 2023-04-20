up: [[Pluginy Gradle]]
X: [[Pluginy binarne Gradle]]

**Pluginy skryptowe są automatycznie znajdowane** (_ang. resolved_) **i stosowane** _(ang. applied)_ **w momencie dodania ich definicji do pliku `build.gradle`.** Można je dodać dla całego projektu, jak i dla wybranego modułu.

```kotlin
apply(from = "other.gradle.kts")
```

Argumentem dla parametru _from_ może być ścieżka względna do pliku lub HTTPS URL

---
https://docs.gradle.org/current/userguide/plugins.html#sec:script_plugins