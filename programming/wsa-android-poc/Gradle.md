### Gradle 
Narzędzie do budowania projektów.
Ma w sobie predefiniowane **taski**, które odpowiadają za np. kompilację plików źródłowych albo generowanie artefaktów (plików wykonywalnych w zależności od platformy).

Na Androidzie kilka takich tasków wywołuje się następująco:

```bash
sh "./gradlew assembleSourceCodeDebug" - skompilowanie kodu
sh "./gradlew testSourceCodeDebugUnitTest" - przejście testów jednostkowych
sh "./gradlew compileSourceCodeDebugAndroidTestSource" - przejście testów instrumentalnych
```

Rzecz jasna najpierw trzeba przejść do folderu zawierającego gradlew, ale generalnie wszystkie taski wykonują się poprzez gradlew.