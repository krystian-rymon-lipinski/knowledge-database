up: [[013.7 Dagger]]

**Umożliwia tworzenie dependencji, których Dagger nie jest w stanie wygenerować automatycznie poprzez konstruktor klasy oznaczonej annotacją `@Inject` - najczęściej dlatego, że obiektów tych nie da się utworzyć przez konstruktor.** 

Dependencje te zwraca się poprzez oznaczenie metod modułu annotacjami:
- `@Provides` - dla instancji tworzonych przez zewnętrzne biblioteki (Retrofit, Room)
- `@Binds` - dla instancji będących implementacją interfejsu

Oba typy muszą być rozdzielone do innych modułów [z pewnych powodów](https://dagger.dev/dev-guide/faq.html#why-cant-binds-and-instance-provides-methods-go-in-the-same-module).

```kotlin
@Module  
class NetworkModule {

@Provides    
fun provideLoginRetrofitService(): LoginRetrofitService {
	return Retrofit.Builder() /* Tworzenie obiektu przez Builder, nie konstruktor */  
		.baseUrl("https://example.com")
		.build()
		.create(LoginService::class.java)
	}
}
...
@Module
abstract class RepositoryModule {

@Binds
abstract fun bindSomeRepository(impl: SomeRepositoryImpl) : SomeRepository
/* Metoda może mieć tylko jeden parametr: typ implementujący interfejs */
}
```

Każdy moduł musi należeć do komponentu.

```kotlin
@Component(modules = [NetworkModule::class])
```

---
https://dagger.dev/dev-guide/faq.html#why-is-binds-different-from-provides