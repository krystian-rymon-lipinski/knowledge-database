up: [[0056 Model-View-ViewModel]]
X: [[0058 LiveData]]
#android/app-architecture/state-holder

**Klasa definiująca [[Przepływ|przepływ]] gorący _(ang. hot flow)_, który może jednocześnie przechowywać stan. Każda zmiana tegoż stanu zostanie przekazana jego obserwatorom.**

```kotlin
/* ViewModel */
private val _uiState = MutableStateFlow(emptyList()) /* Wartość początkowa wymagana */
val uiState: StateFlow<List<Int>> = _uiState
...
_uiState.value = listOf(13, 21, 24)
```

Każdy nowy obserwator w momencie podpięcia pod `StateFlow` otrzymuje ostatnią wartość stanu (i później oczywiście każdą kolejną w momencie jego zmiany). 

**Aby powiązać cykl życia `StateFlow` z jego obserwatorem trzeba użyć funkcji `repeatOnLifecycle`! Bez tego przepływ dla widoku będzie aktywny również jego zamknięciu, co może prowadzić do błędów i _crashów_.**

```kotlin
/* Activity/Fragment */
lifecycleScope.launch {
	repeatOnLifecycle(Lifecycle.State.STARTED) {
		customViewModel.uiState.collect {
			/* Use collected state */
		}
	}
}
```

Bardziej ogólną wersją `StateFlow` jest [ShareFlow](https://developer.android.com/kotlin/flow/stateflow-and-sharedflow#sharedflow).