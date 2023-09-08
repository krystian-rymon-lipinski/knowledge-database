up: [[000 HOME]]
#gradle/plugin

**Wymagany do korzystania z biblioteki [[013.8 Hilt|Hilt]].**

```kotlin
id("com.google.dagger.hilt.android") version "2.44" apply false
```

Zdarza się, że dodanie i zainicjowanie pluginów powoduje błędy w Gradle. Rozwiązaniem okazuje się być dodanie od razu Hiltowych dependencji.