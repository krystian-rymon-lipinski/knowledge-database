up: [[Gradle for Android]]
#status/backlog 
#tech-area/gradle #tech-area/android 

Należy najpierw [[Generowanie klucza dla pliku .apk|wygenerować klucz do podpisu]].
Następnie wewnątrz bloku `android` można zadeklarować:

```kotlin
signingConfigs { 
	create("release") { 
		keyAlias = "my-key-alias" /* Określany podczas tworzenia klucza */
		keyPassword = "my-key-password" /* Hasło dla aliasu */
		storeFile = file("path/to/keystore") /* Ścieżka do pliku .keystore */
		storePassword = "my-store-password" /* Hasło do keystore'a */
	} 
}
```

I wykorzystać w typie buildu:

```kotlin
buildTypes { 
	getByName("release") { 
		signingConfig = signingConfigs.getByName("release") 
	} 
}
```
