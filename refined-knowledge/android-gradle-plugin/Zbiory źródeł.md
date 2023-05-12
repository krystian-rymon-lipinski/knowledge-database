up: [[071 Android Gradle Plugin MOC]]

**Zbiór źródeł *(ang. source set)* to nic innego jak folder zawierający kod źródłowy i zasoby projektu.** Dla każdego nowego modułu androidowego Android Studio automatycznie tworzy foldery, z których korzystają wszystkie warianty *buildu*:
- `src/main` - dla plików źródłowych implementacji
- `src/test` - dla plików źródłowych [[014 Android Testing|testów lokalnych]]
- `src/androidTest` - dla plików źródłowych [[014 Android Testing|testów instrumentacyjnych]]

Wewnątrz modułu można również zdefiniować dodatkowe foldery zgodnie z następującą logiką:
- `src/<flavor_name>/` - dla plików źródłowych implementacji konkretnego [[Flavory projektu Android|flavoru]] 
- `src/test<build_type_name>` - dla plików źródłowych testów jednostkowych konkrentego [[Typy buildu projektu Android|typu buildu]]
- `src/androidTest<flavor_name><build_type_name>/` - dla plików źródłowych testów instrumentacyjnych konkretnego [[Warianty projektu Android|wariantu]], etc...

Najprościej utworzyć nowy folder odpowiadający nazwą poprzez klik PPM w folder `src` i wybranie `New -> Directory`. Android Studio pokaże listę dostępnych nazw folderów bazując na aktualnie zdefiniowanych wariantach.

W każdym takim folderze można utworzyć następujące podfoldery:
- `java` - kod źródłowy w Javie (ale i Kotlinie też)
- `kotlin` - kod źródłowy w Kotlinie
- `res` - [[Zasoby projektu Android|zasoby projektu Android]]
- `resources`
- `rs` - RenderScript (podobno)
- `shaders`
- `assets`
- `aidl`

[[Zadania Gradle AGP|Zadanie AGP]] `./gradlew sourceSets` pozwala podejrzeć oczekiwaną przez Gradle strukturę folderów wariantu (domyślną). Można ją zmienić na [własną](https://developer.android.com/build/build-variants#configure-sourcesets) przez blok `sourceSets { }`.