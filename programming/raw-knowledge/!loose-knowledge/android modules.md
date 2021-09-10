android-modules


Aplikacja androida MUSI mieć przynajmniej jeden moduł aplikacji, definiowany w Gradle'u poprzez:

apply plugin: 'com.android.application'

Zbudowanie takiego modułu spowoduje utworzenie pliku .APK.

Moduł aplikacji nie może mieć w swoich dependencjach innego modułu aplikacji. Może mieć tylko moduł biblioteki, definiowany w Gradle'u poprzez:

apply plugin: 'com.android.library'

Zbudowanie takiego modułu spowoduje utworzenie pliku .AAR. (Podobny to .JAR, ale ma jeszcze np. resources.)


#tech-area/android 