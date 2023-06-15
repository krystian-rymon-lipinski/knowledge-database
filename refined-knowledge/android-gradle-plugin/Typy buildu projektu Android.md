up: [[061 Android Gradle Plugin MOC]]
X: [[Flavory projektu Android]]

**Jeden z elementów [[Warianty projektu Android|wariantu]]. Pozwala tworzyć różne wersje tej samej aplikacji.** Domyślnie Android Gradle Plugin dostarcza dwa typy *buildu*: *debug* i *release*. Można też tworzyć własne.

```kotlin
buildTypes {
	getByName("release") {  
	    ...
	create("customBuildType") {
		initWith(getByName("debug")) /* Skopiowanie konfiguracji z innego typu buildu */
		...
	}
}
```

Każdy typ *buildu* może nadpisać następujące własności domyślnej [[Konfiguracja projektu Android|konfiguracji]]:
- `applicationIdSuffix` - zdefiniowanie różnych wartości dla różnych typów *buildów* pozwala na zainstalowanie każdej z nich na tym samym urządzeniu (zamiast jej nadpisania)
- `versionNameSuffix`
- `isDebuggable` - domyślnie `true` dla wersji *debug*
- `signingConfig` - umożliwia [[Podpisywanie pliku .apk|podpisanie pliku .apk]]
- `proGuardFiles` - umożliwia [[Zaciemnianie kodu źródłowego|zaciemnianie kodu źródłowego]]

[Optymalizowanie](https://developer.android.com/build/shrink-code) jest możliwe poprzez:
- `isMinifyEnabled` - powoduje usuwanie nieużywanego kodu
- `isShrinkResources` - powoduje usuwanie nieużywanych zasobów


