up: [[Przechowalnik stanu ekranu]]

Produkcja stanu ekranu odbywa się poprzez transformację przepływów zimnych, eksponujących dane z warstwy danych, w gorące (a konkretnie StateFlow) - poprzez operator `stateIn`. Można również łączyć kilka przepływów poprzez `combine()`.

```kotlin
class InterestsViewModel(    
	authorsRepository: AuthorsRepository
) : ViewModel() {
val uiState = authorsRepository.getAuthorsStream()
	.stateIn(
		scope = viewModelScope, 
		started = SharingStarted.WhileSubscribed(), 
		initialValue = emptyListOf<Author)()
	)
}
```

**Nie powinno się produkować pierwotnych wartości stanu poprzez blok `init` lub konstruktor ViewModelu!** Po to właśnie definiuje się `initialValue` w metodzie `stateIn`. Jeżeli nie jest to możliwe, należy zaimplementować otwartą metodę `initialize()` wołaną z zewnątrz, ustawiającą wartość stanu.

**Poprawne testowanie operatora `.stateIn` jest problematyczne ze względu na to, że w testach nie sposób kontrolować kolejności emitowania i konsumowania kolejnych stanów.** Z tego powodu niemożliwe jest sprawdzanie każdego kolejnego stanu, a i poleganie tylko na jego końcowej wartości również jest niedeterministyczne.

> [!NOTE] W oczekiwaniu na jakiś TestObserver, załatwiający tę kwestię.

---
https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/state-in.html