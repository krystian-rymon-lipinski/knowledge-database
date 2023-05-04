up: [[070 Gradle MOC]]

Są to skrypty budujące projekt Gradle. Definiują [domyślne importy](https://gradle.github.io/kotlin-dsl-docs/api/org.gradle.kotlin.dsl/-kotlin-build-script/index.html).

#### `settings.gradle`

**Definiuje strukturę projektu.** Należy w nim zadeklarować wszystkie subprojekty i moduły, które powinny zostać użyte do budowania projektu, relacje między nimi oraz właściwości, które są dla nich wszystkich wspólne (jeśli takowe są). Dodanie choćby jednego subprojektu oznacza, że mamy do czynienia z [[Wieloprojektowy build|wieloprojektowym buildem]].

Można zrezygnować z tworzenia tego pliku, ale tylko w przypadku projektu bez subprojektów. Należy też mieć mna uwadze, że zaimplementowane zostaną wówczas domyślne ustawienia.

#### `build.gradle`

**Plik niezbędny dla prawidłowego zbudowania projektu Gradle!** Jest to główny plik konfiguracyjny (znajdujący się w głównym folderze projektu), który może zawierać konkretne zadania, potrzebne dependencje, ustawienia (np. wersja JDK) oraz wszelkie inne polecenia opisujące *build* projektu.

**Jako że każdy subprojekt ma swój własny plik `build.gradle,` w tym pliku należy definiować tylko najogólniejsze ustawienia wspólne dla całego projektu, tj. wszystkich jego modułów** (np. publiczne repozytoria i/lub wykorzystywane pluginy).

Dla głównego pliku nazwanego inaczej niż `build.gradle`, trzeba go najpierw ustawić:

```bash
./gradlew -b otherName.gradle
```
