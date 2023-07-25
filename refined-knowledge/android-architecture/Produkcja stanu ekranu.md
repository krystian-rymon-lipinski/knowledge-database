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

---
https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/state-in.html