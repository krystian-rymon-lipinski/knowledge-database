up: [[Jetpack Compose]]
#status/1-in-progress
#tech-area/android/ui

**Funkcja komponowalna może posiadać stan _(ang. stateful)_ lub być bezstanowa _(ang. stateless)_.**

Definiowanie stanu dla funkcji komponowalnych jest możliwe poprzez `mutableStateOf()`, należy przy tym podać wartość początkową stanu. Każda jej zmiana spowoduje rekompozycję funkcji komponowalnej, która zawiera ten stan - Compose obserwuje tę zmianę i reaguje na nią.

Aby jednak móc zapamiętać tę zmianę stanu i nie utracić jej z powodu rekompozycji, należy skorzystać z funkcji komponowalnej `remember { }`. 

```kotlin
val state: MutableState<ComplexState?> = remember { mutableStateOf(null) }
```

Stan zapamiętany przez funkcję `remember {}` nie przetrwa [[Zmiany konfiguracyjne Android|zmian konfiguracyjnych]], do tego należy użyć funkcji `rememberSaveable {}`. Dla bardziej złożonego obiektu, trzeba zdefiniować, jak ma się on zapisywać i odtwarzać poprzez `Saver` oraz jego wyspecjalizowane implementacje: `listSaver`, `mapSaver`. Może to wymagać [[Parcelable|parcelowania]] składowych stanu.

Jeżeli zostanie wywołane więcej instancji konkretnej funkcji komponowalnej, każdy jej egzemplarz będzie posiadał swój własny stan.

- [[Podnoszenie stanu w Compose|podnoszenie stanu]]
- [[Stan logiki UI|stan logiki UI]]


---

Można z tego stanu utworzyć Flow poprzez `snapshotFlow`. Wówczas wyemitowana zostanie wartość, za każdym razem, gdy wartość wewnątrz tej funkcji się zmieni.

```kotlin
snapshotFlow { editableUserInputState.text }  
    .filter { !editableUserInputState.isHint }  
    .collect {  
        currentOnDestinationChanged(editableUserInputState.text)  
    }
```

Istnieje jeszcze `derivedStateOf` - powoduje to takie coś, że rekompozycja wywoła się tylko wtedy, gdy wartość stanu będzie różna od poprzednio zapamiętanej:

```kotlin
val showButton by remember 
	{ derivedStateOf 
		{ listState.firstVisibleItemIndex > 0 /* Samo firstVisibleItemIndex woła się zawsze, gdy ten index się zmienia */
	}
}
```



###### [[Przechowalnik stanu ekranu]]:

Chodzi o to, aby stan przechowywany w innych klasach `StateFlow`, `LiveData`, etc. przekonwertować na klasę `State` z Compose.

- `colletAsStateWithLifecycle` - kolekcjonowanie zmian emitowanych przez StateFlow, zgodnie z aktualnym cyklem życia komponentu; (czyli np. odbieranie danych z flow będzie cancelowane dla aplikacji będącej w tle); wymaga biblioteki: 
 `implementation "androidx.lifecycle:lifecycle-runtime-compose:$lifecycle_version"`;

- `observeAsState` - dla LiveData
- `subscribeAsState` - dla Observables z RxJavy


```kotlin
val uiState = viewModel.uiState.collectAsStateWithLifecycle()
```

Za kulisami ta funkcja używa `produceState()`, której też można użyć do produkcji stanu. Odpala ona korutynę i za parametry przyjmuje wartość początkową oraz blok, który najpewniej ma tę wartość zmienić po (być może trwającym chwilę) zczytaniu danych.

---

ViewModel można dostać z każdej funkcji komponowalnej, wołając `viewModel()`. Potrzebna jest do tego dependencja: `implementation("androidx.lifecycle:lifecycle-viewmodel-compose:{latest_version}")`.

Dobrze jest trzymać instancję ViewModelu w Composablu opisującym cały ekran (blisko root composabla), do dolnych komponentów komponowalnych dostarczając tylko konkretne potrzebne elementy ViewModelu.

Ale jeszcze lepiej jest do takiego composabla podać tylko stan ViewModelu, a sam view model zainicjalizować w aktywności (albo w composablu NavHost). Wówczas łatwiej jest go testować oraz możliwy jest preview (jeśli poda się preview z viewModel() jako parametrem, preview nie będzie w stanie tego pokazać).

Można oczywiście również wykorzystać [[@HiltViewModel|HiltViewModel]].

---

Potrzebne dependencje do pracy z ViewModel w Compose:

```kotlin
// Do metody viewModel()
implementation("androidx.lifecycle:lifecycle-viewmodel-compose:2.5.0")
// Do metody collectAsStateWithLifecycle()
implementation("androidx.lifecycle:lifecycle-runtime-compose:2.5.0")
// Do metody hiltViewModel()
implementation("androidx.hilt:hilt-navigation-compose:1.0.0")
```
