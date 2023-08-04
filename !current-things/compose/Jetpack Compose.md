up: [[010 Android MOC]]
#status/1-in-progress
#tech-area/android
#gradle/build-feature #android/gradle-dependency

**Rekomendowany _framework_ do tworzenia [[Interfejs użytkownika|interfejsów użytkownika]] dla natywnych aplikacji Androida oparty na podejściu [[Programowanie deklaratywne vs. imperatywne|deklaratywnym]].** Wymaga [konfiguracji](https://developer.android.com/jetpack/compose/setup#setup-compose) _buildu_ i dependencji w Gradle, która musi być [kompatybilna z Kotlinem](https://developer.android.com/jetpack/androidx/releases/compose-kotlin#pre-release_kotlin_compatibility).

- [[Funkcje komponowalne|funkcje komponowalne]]
- [[Annotacja @Preview]]
- [[Composable modifiers]]
- [[Komponenty i Material Design]]
- [[Layouty Compose]]
- [[Animacje Compose]]

- [[Przechowywanie stanu w Compose]]
- [[Compose Navigation]]

- `setContent { }` - funkcja przyjmująca za parametr funkcję komponowalną - intro do definiowania layoutu; potrzebna jest dependencja: `implementation("androidx.activity:activity-compose:1.7.2")`

Dobrze jest zdefiniować root widok z domyślnym parametrem Modifier - wówczas można go używać jednocześnie w implementacji i preview. W ogóle na potrzeby preview wystarczy zdefiniować domyślne parametry, np. jakiejś listy, czy w ogóle całego stanu.
```kotlin
setContent {  
    MaterialTheme {  
        ExampleScreen(modifier = Modifier.fillMaxSize())  
    }  
}
```
- `ComponentActivity()` - aktywność compose'a?
- Compose BOM - Bill of Materials - taka jakby główna dependencja Compose, która zawiera linki do pozostałych; wówczas nie trzeba podawać wersji we wszyttkich użytkowanych bibliotek, będą one miały wersje [podane w mapowaniu](https://developer.android.com/jetpack/compose/bom/bom-mapping); można to mapowanie z BOM-u oczywiście nadpisać; sam BOM nie dodaje żadnych dependencji do aplikacji, definiuje tylko konkretną wersję do pobrania, gdy w kodzie pojawi się dependencja do biblioteki


---

Część rzeczy jest [[Funkcja wstrzymująca|funkcjami wstrzymującymi]], więc trzeba je wołać z korutyny. Można dostać scope poprzez `rememberCoroutineScope`.

---

Rysowanie w Compose

- `Modifier.drawBehind/drawWithContent/drawWithCache`
- `Canvas { }` - za kulisami Modifier.drawBehind


---
https://developer.android.com/jetpack/compose/documentation