up: [[071 Android Gradle Plugin MOC]]

**Definiowanie androidowych właściwości projektu Gradle potrzebnych do kompilacji, budowania oraz obecności aplikacji w [[011 Google Play Store|Google Play Store]]**.

```kotlin
android {  
    namespace = "com.krystianrymonlipinski.testexercise" /* Potrzebne do wygenerowania nazwy paczki dla klas R i BuildConfig */
    compileSdk = 33   /* Numer API Androidowego, powinien być najwyższy możliwy, żeby uwzględniać najnowsze zmiany Android API. Mają kompatybilność wsteczną. */
    buildToolsVersion = "33.0.2" /* Wersja narzędzi do budowania, powinny być najnowsze możliwe. Mają kompatybilność wsteczną. */

	defaultConfig {  
		applicationId = "com.krystianrymonlipinski.testexercise" /* Unikalna nazwa na potrzeby Google Play Store. NIE MOŻNA JEJ ZMIENIAĆ, BO INACZEJ UŻYTKOWNICY NIE BĘDĄ WIDZIEĆ UPDATE'ÓW! */
		minSdk = 21  /* Najniższa wersja Android API, którą wspiera aplikacja. Urządzenia z niższym SDK nie będą jej widzieć w Google Play Store */
		targetSdk = 33 /* Wersja Androida zamierzona dla tej aplikacji */
		versionCode = 1  /* Wersja aplikacji. Inkrementowana dla każdej kolejnej paczki rzucanej do Google Play Store */
		versionName = "1.0"  /* Aktualny numer wersji aplikacji widoczny dla użytkowników. Najczęściej w formacie X.Y.Z (2.4.5, 1.1.10, etc.) */
	  
		testInstrumentationRunner = "androidx.test.runner.AndroidJUnitRunner"  
	}  
}
```

Blok `defaultConfig` opisuje domyślną konfigurację, którą można nadpisać dla konkretnych [[Warianty projektu Android|wariantów projektu]]. Można w nim zdefiniować dodatkowe wartości:
- `applicationIdSuffix`
- `versionNameSuffix`
- `signingConfig`
- `proGuardFiles`
- `testApplicationId`
- `testNamespace` (domyślnie `<namespace>.test`)

Numer najnowszej wersji [[Android Build Tools]] można znaleźć [tutaj](https://developer.android.com/tools/releases/build-tools#kts). Dla wersji AGP 3.0.0+ nie trzeba jej deklarować, plugin sam sobie ściągnie najnowszą.