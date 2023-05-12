up: [[071 Android Gradle Plugin MOC]]
X: [[Typy buildu projektu Android]]

**Jeden z elementów [[Warianty projektu Android|wariantu]]. Pozwala tworzyć różne wersje tej samej aplikacji. Każdy z nich musi należeć do [[Grupy flavorów|grupy]].**

Każdy *flavor* może nadpisać następujące własności domyślnej [[Konfiguracja projektu Android|konfiguracji]]:
- `applicationId`
- `applicationIdSuffix`
- `versionCode`
- `versionName`
- `versionNameSuffix`
- `targetSdkVersion`
- `minSdkVersion`
- `signingConfig` - umożliwia [[Podpisywanie pliku .apk|podpisanie pliku .apk]]
- `proGuardFiles` - umożliwia [[Zaciemnianie kodu źródłowego|zaciemnianie kodu źródłowego]]

Zmiana `applicationId` (lub dodanie do niego *suffixu*) powoduje, że można zainstalować na urządzeniu różne *flavory* jednocześnie.

```kotlin
productFlavors { 
	create("flavor1") { 
		dimension = "first-dim" /* Zdefiniowanie grupy flavoru */
		applcationIdSuffix = ".flavor1"
	}
}
```

