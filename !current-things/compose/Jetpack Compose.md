up: [[010 Android MOC]]
#status/1-in-progress
#tech-area/android
#gradle/build-feature #android/gradle-dependency

**Rekomendowany _framework_ do tworzenia [[Interfejs użytkownika|interfejsów użytkownika]] dla natywnych aplikacji Androida oparty na podejściu [[Programowanie deklaratywne vs. imperatywne|deklaratywnym]].** Wymaga [konfiguracji](https://developer.android.com/jetpack/compose/setup#setup-compose) _buildu_ i dependencji w Gradle, która musi być [kompatybilna z Kotlinem](https://developer.android.com/jetpack/androidx/releases/compose-kotlin#pre-release_kotlin_compatibility).

- [[Funkcje komponowalne|funkcje komponowalne]]
- [[Annotacja @Preview|annotacja @Preview]]
- [[Modyfikatory funkcji komponowalnych|modyfikatory funkcji komponowalnych]]

- [[Stan funkcji komponowalnych|stan funkcji komponowalnych]]
---
- [[Komponenty i Material Design]]
- [[Layouty Compose]]
- [[Animacje Compose]]

- [[Compose Navigation]]
- [[Testowanie w Compose]]


- `ComponentActivity()` - aktywność compose'a? ComponentActivity() zamiast AppCompatActivity()
- Compose BOM - Bill of Materials - taka jakby główna dependencja Compose, która zawiera linki do pozostałych; wówczas nie trzeba podawać wersji we wszyttkich użytkowanych bibliotek, będą one miały wersje [podane w mapowaniu](https://developer.android.com/jetpack/compose/bom/bom-mapping); można to mapowanie z BOM-u oczywiście nadpisać; sam BOM nie dodaje żadnych dependencji do aplikacji, definiuje tylko konkretną wersję do pobrania, gdy w kodzie pojawi się dependencja do biblioteki

---

Side-effect to zmiana stanu aplikacji dokonująca się poza funkcją komponowalną.

---

Część rzeczy jest [[Funkcja wstrzymująca|funkcjami wstrzymującymi]], więc trzeba je wołać z korutyny. 

Odpalić korutynę można poprzez `LaunchedEffect { }`. Definiuje ona klucze, które przy zmianie ich wartości powodują zrestartowanie korutyny. Można podać stałą jako klucz (np. Unit), wówczas wykona się ona tylko raz. Można również zapisać wartość klucza (gdyby miała się w przyszłości zmienić i coś popsuć) poprzez `rememberUpdatedState`.

Korutynę można również odpalić na zasięgu dostanego poprzez `rememberCoroutineScope()`. Zasięg ten jest związany z kompozycją, gdzie został zdefiniowany i ginie wraz z nią.

LaunchedEffect TRZEBA odpalić z Composable'a. `rememberCoroutineScope` również, ale samą korutynę już nie.


Odmianą `LaunchedEffect` jest `DisposableEffect` - różni się o tyle, że może zadeklarować w sobie `onDispose {}` i posprzątać jakieś zasoby.

---

Rysowanie w Compose

- `Modifier.drawBehind/drawWithContent/drawWithCache`
- `Canvas { }` - za kulisami Modifier.drawBehind

---

Można pytać o dokładne położenie elementu na ekranie poprzez `Modifier.onGloballyPositioned`. Argumentem lambdy jest obiekt `LayoutCoordinates`, poprzez którego można pytać o położenie elementu względem rodzica, korzenia lub całego okna. **Zwracane wartości koordynatów są w PIKSELACH, nie w dp!**

---

https://developer.android.com/jetpack/compose/documentation