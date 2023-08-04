up: [[Jetpack Compose]]
#status/1-in-progress
#tech-area/android/ui

###### [[Przechowalnik stanu logiki UI]]:

Zapisywanie stanu UI (np. zaznaczone RadioButtony) jest możliwe poprzez:

```kotlin
var selectedAnswer: MutableState<Answer?> = remember { mutableStateOf(null) }
```

Zmiana stanu spowoduje rekompozycję wszystkich funkcji komponowalnych, które korzystają z tego stanu podczas generowania UI. Jeśli rekompozycja zostanie wywołana z innych względów (np. przez odegranie animacji) **stan się nie zmieni (ani nie "wyzeruje").** Stan nie przetrwa natomiast [[Zmiany konfiguracyjne Android|zmian konfiguracyjnych]], ale do tego wystarczy zawołać `rememberSaveable`.

Jeżeli będzie wołane więcej tej samej funkcji komponowalnej, każdy egzemplarz będzie miał swój stan.

Stan powinien być zdefiniowany i trzymany w Composeablu najniżej w hierarchii widoków jak to tylko możliwe i tylko w tym jednym miejscu zmieniany (Single Source of Truth principle). Aczkolwiek czasem może się zdarzyć, że więcej node'ów UI zależy od tego samego stanu, wówczas posiadaczem stanu należy uczynić rodzica tych node'ów, a do nich samych podać callback, którego definicja (akcja do wykonania, np. na klik) zdefiniowana będzie w rodzicu.
###### [[Przechowalnik stanu ekranu]]:

Zapisywanie stanu aplikacji dzieje się przez StateFlow, a subskrybowanie go przez Compose w następujący sposób:

```kotlin
val uiState = viewModel.uiState.observeAsState()
```