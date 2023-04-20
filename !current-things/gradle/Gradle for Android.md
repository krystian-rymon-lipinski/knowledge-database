up: [[070 Gradle MOC]]
#status/in-progress 
#tech-area/gradle 


https://developer.android.com/build

- settings.gradle - zarządzanie modułami
```groovy
include(":<module_name")
```
- build.gradle
- <module_name>/build.gradle


Android Gradle Plugin definiuje dodatkowy blok kodu, `android`:

```kotlin
android {  
    namespace = "com.krystianrymonlipinski.testexercise"  
    compileSdk = 33   /* Numer API, powinien być najwyższy możliwy, żeby uwzględniać najnowsze zmiany Android API. Mają kompatybilność wsteczną. */
    buildToolsVersion = "33.0.2" /* Wersja narzędzi do budowania, powinny być najnowsze możliwe. Mają kompatybilność wsteczną. */
  
    defaultConfig {  
        applicationId = "com.krystianrymonlipinski.testexercise" /* Unikalna nazwa na potrzeby Google Play Store. NIE MOŻNA JEJ ZMIENIAĆ! UŻYTKOWNICY NIE BĘDĄ WIDZIEĆ UPDATE'ÓW! */
        minSdk = 21  /* Najniższa wersja Android API, którą wspiera aplikacja. Urządzenia z niższym SDK nie będą jej widzieć w Google Play Store */
        targetSdk = 33 /* Wersja Androida zamierzrona dla tej aplikacji */
        versionCode = 1  /* Wersja aplikacji. Inkrementowana dla każdej kolejnej paczki rzucanej do Google Play Store */
        versionName = "1.0"  /* Aktualna numer wersji aplikacji widoczny dla użytkowników. Najczęściej w formacie X.Y.Z (2.4.5, 1.1.10, etc.) */
  
        testInstrumentationRunner = "androidx.test.runner.AndroidJUnitRunner"  
    }  
  
    buildTypes {  
        getByName("release") {  
            isMinifyEnabled = false  
            proguardFiles(getDefaultProguardFile("proguard-android-optimize.txt"), "proguard-rules.pro")  
        }  
    }    buildFeatures {  
        viewBinding = true  
    }  
  
    compileOptions {  
        sourceCompatibility = JavaVersion.VERSION_1_8  
        targetCompatibility = JavaVersion.VERSION_1_8  
    }  
    kotlinOptions {  
        jvmTarget = "1.8"  
    }  
}
```

Ostatnią `buildToolsVersion` można znaleźć [tutaj](https://developer.android.com/tools/releases/build-tools#kts). Jeżeli pobrany jest [[Android Gradle Plugin]] 3.0.0+, nie trzeba deklarować, on sam sobie ściągnie najnowszą.

Ogólnie to defaultConfig jest do podglądnięcia w File -> Project Structure w [[012 Android Studio MOC]]


