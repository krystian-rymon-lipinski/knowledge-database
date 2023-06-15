up: [[061 Android Gradle Plugin MOC]]

**Wszystkie [[Plik wykonywalny .apk|pliki .apk]] muszą zostać podpisane, jeśli mają zostać zainstalowane na urządzeniu!**

Wersja *debug* aplikacji jest podpisywana przez androida. Klucz ten znajduje się w lokalizacji domyślnej użytkownika po folderem .android (dla windowsa: `C:\Users\<user>\.android`). Jest to plik `debug.keystore`, który chroniony jest hasłem: "android". Typ tego klucza to JKS - Java KeyStore.

Klucz ten posiada certyfikat o aliasie: "androiddebugkey". Ten właśnie certyfikat jest używany do podpisywania pliku .apk w wersji debug, kiedy jest on instalowany na urządzeniu.


Dla wersji *release* (i każdej innej własnej) należy [[Generowanie klucza dla pliku .apk|wygenerować swój własny klucz]]. Następnie wewnątrz bloku `android` można zadeklarować konfigurację podpisu i wykorzystać ją w później w typie *buildu* lub *flavorze*:

```kotlin
signingConfigs { 
	create("release") { 
		keyAlias = "my-key-alias" /* Określany podczas tworzenia klucza */
		keyPassword = "my-key-password" /* Hasło dla aliasu */
		storeFile = file("path/to/keystore") /* Ścieżka do pliku .keystore */
		storePassword = "my-store-password" /* Hasło do keystore'a */
	} 
	create("anotherSigningConfig") {
		...
	}
}
...
buildTypes { 
	getByName("release") { 
		signingConfig = signingConfigs.getByName("release") 
	} 
	create("customBuildType") {
		signingConfig = signingConfigs.getByName("anotherSigningConfig") 
	}
}
...
productFlavors {
	create("customFlavor") {
		signingConfig = signingConfigs.getByName("release") 
	}
}
```





