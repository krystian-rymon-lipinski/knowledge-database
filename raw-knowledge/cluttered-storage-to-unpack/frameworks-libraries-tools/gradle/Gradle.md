#status/backlog 
#tech-area/gradle

**Narzędzie do budowania projektów.**
Ma w sobie predefiniowane **taski**, które odpowiadają za np. kompilację plików źródłowych albo generowanie artefaktów (plików wykonywalnych w zależności od platformy).

Na Androidzie kilka takich tasków wywołuje się następująco:

```bash
sh "./gradlew assembleSourceCodeDebug" - skompilowanie kodu
sh "./gradlew testSourceCodeDebugUnitTest" - przejście testów jednostkowych
sh "./gradlew compileSourceCodeDebugAndroidTestSource" - przejście testów instrumentalnych
```

Rzecz jasna najpierw trzeba przejść do folderu zawierającego gradlew, ale generalnie wszystkie taski wykonują się poprzez gradlew.

---
**Wersja Gradle'a zależy od wersji Kotlina!**
https://kotlinlang.org/docs/gradle-configure-project.html#apply-the-plugin
**Ponadto trzeba zdefiniować wersję [[Android Gradle Plugin]]!**
https://developer.android.com/build/releases/gradle-plugin#updating-gradle

---
W gradle'u można zdefiniować **dependencje** - biblioteki i frameworki, od których zależy nasz projekt.

```groovy
dependencies {  } /* Top level declaration in build.grale for module */
```

https://search.maven.org/ - strona, gdzie można wyszukać potrzebne dependencje
[[Przykłady pluginów i dependencji gradle z ich znaczeniami]]

---
