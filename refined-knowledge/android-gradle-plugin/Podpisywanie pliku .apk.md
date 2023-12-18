up: [[061 Android Gradle Plugin MOC]]
#status/0-revision-needed 

**Wszystkie [[Plik wykonywalny .apk|pliki .apk]] muszą zostać podpisane, jeśli mają zostać zainstalowane na urządzeniu!**

Wersja *debug* aplikacji jest podpisywana przez androida. Klucz ten znajduje się w lokalizacji domyślnej użytkownika po folderem .android (dla windowsa: `C:\Users\<user>\.android`). Jest to plik `debug.keystore`, który chroniony jest hasłem: "android". Typ tego klucza to JKS - Java KeyStore.

Klucz ten posiada certyfikat o aliasie: "androiddebugkey". Ten właśnie certyfikat jest używany do podpisywania pliku .apk w wersji debug, kiedy jest on instalowany na urządzeniu.


Dla wersji *release* (i każdej innej własnej) należy [[Generowanie klucza dla pliku .apk|wygenerować swój własny klucz]]. Następnie wewnątrz bloku `android` można zadeklarować konfigurację podpisu i wykorzystać ją w później w typie *buildu* lub *flavorze*:

```kotlin
signingConfigs { 
	create("release") { 
		...
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
```

Dobrze jest nie wpisywać kluczy i haseł "z palca", ponieważ są to dane wrażliwe, których nie należy wysyłać na serwer. W to miejsce można utworzyć nowy plik _.properties_, ignorowany przez Gita:

```makefile
keystoreFile=path\\to\\keystore  
keystorePassword=password
keyAlias=alias
keyPassword=keyPassword
```

I dane zapisane tam wyszukać w skrypcie Gradle:

```kotlin
signingConfigs {  
	create("release") {  
		val keystorePropertiesFile: File = rootProject.file("keystore.properties")  
		val keystoreProperties = Properties()  
		keystoreProperties.load(FileInputStream(keystorePropertiesFile))  
  
		storeFile = file(keystoreProperties["keystoreFile"].toString())  
		keyAlias = keystoreProperties["keyAlias"].toString()  
		storePassword = keystoreProperties["keystorePassword"].toString()  
		keyPassword = keystoreProperties["keyPassword"].toString()  
	}  
}
```

Jeżeli istnieje zautomatyzowany _pipeline_ do dostarczania aplikacji na produkcję, trzeba jakoś dostarczyć wrażliwe dane w taki sposób, by mógł z nich skorzystać bez jednoczesnego udostępniania ich wszystkim na repozytorium (np. poprzez _secrets_ w GitHub Actions, każda platforma będzie oferowała inne możliwości).