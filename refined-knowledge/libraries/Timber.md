#android/gradle-dependency 

**Biblioteka do logowania.**

```kotlin
implementation 'com.jakewharton.timber:timber:5.0.1'
```

Operuje na drzewach, które dobrze jest zainstalować jak najszybciej po wejściu do aplikacji.

```kotlin
class TestExerciseApplication : Application() {  
    override fun onCreate() {  
        super.onCreate()  
  
        if (BuildConfig.DEBUG) {  
            Timber.plant(Timber.DebugTree())  
        }  
    }  
}
```

Ponadto,  zeby działało, trzeba dodać w manifeście nazwę aplikacji:
```xml
<application  
    android:name=".TestExerciseApplication" >
</application>
```

---
https://github.com/JakeWharton/timber