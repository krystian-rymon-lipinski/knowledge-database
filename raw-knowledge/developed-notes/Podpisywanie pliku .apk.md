up: [[Plik wykonywalny .apk]]
#status/freezer 
#tech-area/android 

**Wszystkie pliki .apk muszą zostać podpisane, jeśli mają zostać zainstalowane na urządzeniu!**

Wersja *debug* aplikacji jest podpisywana przez androida. Klucz ten znajduje się w lokalizacji domyślnej użytkownika po folderem .android (dla windowsa: `C:\Users\<user>\.android`). Jest to plik `debug.keystore`, który chroniony jest hasłem: "android". Typ tego klucza to JKS - Java KeyStore.

Klucz ten posiada certyfikat o aliasie: "androiddebugkey". Ten właśnie certyfikat jest używany do podpisywania .apk w wersji debug, kiedy jest ona instalowana na urządzeniu.


Dla wersji *release* należy [[Generowanie klucza dla pliku .apk|wygenerować swój własny klucz]].




