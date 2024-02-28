up: [[061 Android Gradle Plugin MOC]]
#status/3-freezer 
#tech-area/android-gradle-plugin 

**Dodatkowe [[Zadania Gradle|zadania Gradle]] definiowane przez Android Gradle Plugin.**

Przydatne:
- `assemble` - buduje projekt bez instalowania go i tworzy [[Plik wykonywalny .apk|plik wykonywalny .apk]] dla wybranych [[Warianty projektu Android|wariantów projektu]]
- `test` - odpalenie [[014 Android Testing|testów lokalnych]] projektu; dla wariantów konwencja nazewnicza tego zadania to `test<Variant>UnitTest`
- `install<variant_name>` - instaluje konkretny wariant aplikacji na urządzeniu
- `sourceSets` - pokazuje domyślną strukturę [[Zbiory źródeł|zbiorów źródeł]] dla wszystkich wariantów
- `androidDependencies` - pokazuje aktualne zależności w projekcie, łącznie z [[Dependencje tranzytywne|dependencjami tranzytywnymi]]
- `connectedAndroidTest` - odpalenie wszystkich [[014 Android Testing|testów instrumentacyjnych]] dla wszystkich wariantów
- `connectedCheck` - podobne co wyżej, ale chyba współbieżnie dla wszystkich połączonych urządzeń?
- `lint` - statyczna analiza kodu


Wszystkie zadania definiowane przez Gradle i AGP można podejrzeć w [[Narzędzia Android Studio|narzędziu Android Studio]]: Gradle i wykonać, klikając w nie.