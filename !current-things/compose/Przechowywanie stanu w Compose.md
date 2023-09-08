up: [[Jetpack Compose]]
#status/1-in-progress
#tech-area/android/ui

**Modyfikacja stanu to _zdarzenie_.**
**Stan _jest_. Zdarzenia się _wydarzają_.**

Każda zmiana stanu powinna być odzwierciedlona w UI. [[Komponenty UI]] robią to poprzez wszelakie settery, Composables natomiast - poprzez `MutableState` i `State`. Wówczas każda zmiana tego stanu spowoduje rekompozycję tych Composabli, które korzystają z tego stanu (Compose sam to śledzi).

Ale zdefiniowanie `State` to jeszcze nie wszystko. Pozwoli to tylko i wyłącznie inicjalizować stan taką samą wartością podczas rekompozycji. Aby móc dokonywać zmian na stanie, które nie będą tracone podczas rekompozycji, należy skorzystać z funkcji `remember`.

```kotlin
val state: MutableState<State?> = remember { mutableStateOf(null) }
var state: State? by remember { mutableStateOf(null) }
```


Composable, które definiują zmienne przy pomocy `remember`, **posiadają stan**. Można ten stan "przerzucić wyżej" (_ang. state hoisting_). Wówczas zamiast definiować stan wewnątrz compose'abla, w jego parametrach definiuje się aktualną wartość do wyświetlenia oraz lambdę, definiującą reakcję, która jakoś zmieni stan wyżej, która woła composabla.

```kotlin
@Compose
fun NumberDisplayed(currentNumber: Int, onButtonClicked: () -> Unit) { }
```

W taki sposób można tworzyć Composable **pozbawione stanu**.

Stateful - Composable trzymający kawałek stanu, który może się zmieniać w czasie
Stateless - Composable niedefiniujący żadnego stanu


> [!NOTE]
> When hoisting state, there are three rules to help you figure out where state should go:
> 1. State should be hoisted to at _least_ the **lowest common parent** of all composables that use the state (read).
> 2. State should be hoisted to at _least_ the **highest level it may be changed** (write).
> 3. If **two states change in response to the same events** they should be **hoisted to the same level.**
> 
> You can hoist the state higher than these rules require, but if you don't hoist the state high enough, it might be difficult or impossible to follow unidirectional data flow.
> 


###### [[Przechowalnik stanu logiki UI]]:

Zapisywanie stanu UI (np. zaznaczone RadioButtony) jest możliwe poprzez:

```kotlin
var selectedAnswer: MutableState<Answer?> = remember { mutableStateOf(null) }
```

Zmiana stanu spowoduje rekompozycję wszystkich funkcji komponowalnych, które korzystają z tego stanu podczas generowania UI. Jeśli rekompozycja zostanie wywołana z innych względów (np. przez odegranie animacji) **stan się nie zmieni (ani nie "wyzeruje").** Stan nie przetrwa natomiast [[Zmiany konfiguracyjne Android|zmian konfiguracyjnych]], ale do tego wystarczy zawołać `rememberSaveable`.

Jeśli próbujemy przechować jakiś bardziej złożony stan UI w stateHolderze i użyć `rememberSaveable`, trzeba zdefiniować, jak ten obiekt ma się zapisywać i odtwarzać. Można tego dokonać poprzez `Saver` lub jego wyspecjalizowane implementacje: `listSaver`, `mapSaver`.

Przy tworzeniu tegoż stateHoldera też wykorzystuje się `mutableStateOf()`. Może to wyglądać np. tak:

```kotlin
var text by mutableStateOf(initialText)  
    private set
```

---

**Ogólnie ze StateHoldera powinno się korzystać w ten sposób, że zapamiętuje się StateHolder poprzez `rememberSaveable` - najczęściej robi się to w osobnej metodzie i w głównym composablu woła się tylko `remember*StateHolder`. Dla Holdera trzeba też zdefiniować Saver, `listSaver` powinien wystarczyć, bo odtwarzamy tylko parametry podane do holdera (które powinny być Parcelable). I wówczas stan trzyma się poprzez `mutableStateOf()`. **

**Wówczas w głównym composablu pamiętamy tylko klasę StateHolder, która zawiera wszystkie stany w sobie, a ponadto zachowuje te stany podczas zmian konfiguracji.**

```kotlin
val stateHolder = rememberStateHolder(die = die)
...
@Composable  
fun rememberStateHolder(die: Die) : ComplexStateHolder {  
    return rememberSaveable(saver = ComplexStateHolder.Saver) {  
        ComplexStateHolder(state = ComplexState())  
    }  
}
...
class ComplexStateHolder(state: ComplexState) {  
    var state by mutableStateOf(state)

	companion object {  
    val Saver: Saver<ComplexStateHolder, *> = listSaver(  
        save = { listOf(it.state) },  
        restore = { ComplexStateHolder(state = it[0]) }  
    )  
}
```

---

Można z tego stanu utworzyć Flow poprzez `snapshotFlow`. Wówczas wyemitowana zostanie wartość, za każdym razem, gdy wartość wewnątrz tej funkcji się zmieni.

```kotlin
snapshotFlow { editableUserInputState.text }  
    .filter { !editableUserInputState.isHint }  
    .collect {  
        currentOnDestinationChanged(editableUserInputState.text)  
    }
```


Jeżeli będzie wołane więcej tej samej funkcji komponowalnej, każdy egzemplarz będzie miał swój stan.

Stan powinien być zdefiniowany i trzymany w Composeablu najniżej w hierarchii widoków jak to tylko możliwe i tylko w tym jednym miejscu zmieniany (Single Source of Truth principle). Aczkolwiek czasem może się zdarzyć, że więcej node'ów UI zależy od tego samego stanu, wówczas posiadaczem stanu należy uczynić rodzica tych node'ów, a do nich samych podać callback, którego definicja (akcja do wykonania, np. na klik) zdefiniowana będzie w rodzicu.


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

Najsensowniej jest trzymać instancję ViewModelu w Composablu opisującym cały ekran (blisko root composabla), do dolnych komponentów komponowalnych dostarczając tylko konkretne potrzebne elementy ViewModelu.
