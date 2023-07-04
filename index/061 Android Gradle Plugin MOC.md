up: [[000 HOME]]

#gradle/plugin  
#status/3-freezer
#tech-area/android-gradle-plugin 

**[[Pluginy binarne Gradle|Plugin binarny]], rozszerzający możliwości Gradle o funkcjonalności przydatne dla projektów Androidowych**, takich jak podpisywanie plików .apk lub wykonywanie testów instrumentalnych. 

```kotlin
id("com.android.application") version "7.0.0" apply false /* Dla tworzenia aplikacji */
id("com.android.library") version "7.0.0" apply false /* Dla tworzenia biblioteki */
```

**Wersja pluginu musi być [kompatybilna z wersją Gradle](https://developer.android.com/build/releases/gradle-plugin#updating-gradle). W przypadku pisania w Kotlinie należy również sprawdzić [kompatybilność z Kotlin Gradle Plugin](https://kotlinlang.org/docs/gradle-configure-project.html#apply-the-plugin).

**Wszelkie funkcjonalności androidowe należy dodawać w pliku `build.gradle` dla modułu wewnątrz bloku `android { }`**. Alternatywnie można to zrobić poprzez narzędzie [[Struktura projektu|struktura projektu]] w Android Studio.

Funkcjonalności AGP:
- [[Konfiguracja projektu Android]]
- [[Warianty projektu Android]]
- [[Flavory projektu Android]]
- [[Typy buildu projektu Android]]
- [[Zbiory źródeł]]
- [[Podpisywanie pliku .apk]]

- [[Zadania Gradle AGP]]

---
- `android.applicationVariants` - warianty dla plug-inu com.android.application
- `android.libraryVariants` - warianty dla plug-inu com.android.library

Pozostałe bloki do wykorzystania:
├── lint 
├── buildFeatures 
├── dataBinding 
├── compileSdkVersion 
├── buildToolsVersion 
├── ndkVersion 
├── externalNativeBuild 
├── sourceCompatibility 
├── targetCompatibility 
├── testOptions - poprzez `resultsDir` można zmienić lokalizację generowania rezultatów testów; domyślna wartość to `build/test-results`
├── jacoco 
├── adbOptions - przydatne np. przy zwiększaniu timeoutu, jeśli na deploy rzeczy dzieją się długo (i wywalają ShellCommandUnresponsiveException)
├── advancedProfilingTransforms 
├── bundle 
└── composeOptions

└── dexOptions - nested w `buildTypes` albo `productFlavors`; daje możliwość kontrolowania procesu konwersji kodu bajtowego Javy (plików .class) do plików wykonywalnych .dex


```kotlin
android {  
    ...
	buildFeatures {  
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

---
https://developer.android.com/reference/tools/gradle-api
https://developer.android.com/build