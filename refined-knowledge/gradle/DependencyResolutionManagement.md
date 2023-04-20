up: [[Dependencje Gradle]]

**API dostępne od wersji 6.8 Gradle.**

```kotlin
/* settings.gradle */
dependencyResolutionManagement {  
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)  
    repositories {  
        google() /* Przykładowe repozytrium publiczne */
    }  
}
```

`RepositoriesMode` decyduje, czy zdefiniowanie dodatkowych repozytoriów w pliku `build.gradle` jest dopuszczalne, czy też powinno skończyć się wyrzuceniem błędu.