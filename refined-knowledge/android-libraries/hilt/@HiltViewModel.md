up: [[013.8 Hilt]]

**Annotacja ułatwiająca wstrzykiwanie ViewModelu do komponentów cyklu życia aplikacji. Umożliwia tworzenie konstruktora z parametrami bez zmian w tworzeniu samego obiektu (i bez konieczności tworzenia fabryki).**

```kotlin
@AndroidEntryPoint
class SomeActivity : AppCompatActivity() {
	private val viewModel: SomeViewModel = ViewModelProvider(this).get(SomeViewModel::class.java)
}

...
@HiltViewModel  
class SomeViewModel @Inject constructor(  
    private val httpService: HttpService  
) : ViewModel() {
```