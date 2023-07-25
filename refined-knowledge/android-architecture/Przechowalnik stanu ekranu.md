up: [[Warstwa UI]]

**Zawiera wszystkie dane aplikacji (pobrane z warstwy danych) potrzebne do wyświetlenia informacji na konkretnym ekranie.** Stan ekranu powinien móc przetrwać [[Zmiany konfiguracyjne Android|zmiany konfiguracyjne]], dlatego najczęściej umieszcza się go w [[0076 ViewModel|ViewModelu]], a przechowywany jest w niemutowalnym obiekcie typu [[0058 LiveData|LiveData]] lub [[StateFlow|StateFlow]]. Jego zmiany są obserwowane przez komponenty cyklu życia tak długo, jak długo istnieje ViewModel, który go zawiera.

```kotlin
class CustomViewModel @Inject constructor (val someRepository: SomeRepository) {
	private val _uiState = MutableStateFlow<ScreenState> = ScreenState()
	val uiState = StateFlow<ScreenState> = _uiState.asStateFlow()
}
```

- [[Modelowanie stanu ekranu|modelowanie stanu ekranu]]
- [[Produkcja stanu ekranu|produkcja stanu ekranu]]
