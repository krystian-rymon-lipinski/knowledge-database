#status/3-freezer 
#tech-area/android 
#android/modularity

android-modules

[[Wieloprojektowy build]]


Aplikacja androida MUSI mieć przynajmniej jeden moduł aplikacji, definiowany w [[070 Gradle MOC]] poprzez:

apply plugin: 'com.android.application'

Zbudowanie takiego modułu spowoduje utworzenie pliku .APK.

Moduł aplikacji nie może mieć w swoich dependencjach innego modułu aplikacji. Może mieć tylko moduł biblioteki, definiowany w Gradle'u poprzez:

```groovy
apply plugin: 'com.android.library'
```

Zbudowanie takiego modułu spowoduje utworzenie pliku .AAR. (Podobny do .JAR, ale ma jeszcze np. resources.)