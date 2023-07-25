up: [[Przechowalnik stanu ekranu]]

Poza wyświetlanymi danymi stan powinien też zawierać informacje o ewentualnych operacjach w trakcie lub błędach - aby ekran mógł przekazać użytkownikowi również takie informacje. 

```kotlin
sealed class State {
	class Idle(loadedData: Data) : State()
	class Loading() : State()
	class Error(message: String) : State()
}
```

Można zamodelować stan przy pomocy większej ilości pól-kontenerów - w zależności od tego, w jaki sposób powiązane są dane. Przy opisywaniu stanu jedną klasą danych każdorazowa jego zmiana będzie powodowała odświeżanie wszystkich powiązanych z nim widoków. 

Przy większej ilości danych problem ten wystąpi niezależnie od definicji stanu. Jedno lub więcej pól-kontenerów będzie zawierało coraz więcej danych, co będzie powodowało aktualizację wszystkich widoków powiązanych z kontenerem. Można temu zapobiec poprzez kontrolowanie poszczególnych składowych `Flow`:

```kotlin
viewModel.uiState
	.map { it.isFetchingArticles }
	.distinctUntilChanged()
	.collect { progressBar.isVisible = it }
```

---
https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/distinct-until-changed.html