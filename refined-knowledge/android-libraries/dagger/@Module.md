up: [[013.7 Dagger]]

**Umożliwia tworzenie dependencji, których Dagger nie jest w stanie wygenerować automatycznie poprzez konstruktor klasy oznaczonej annotacją `@Inject` - najczęściej dlatego, że obiektów tych nie da się utworzyć przez konstruktor.** Metoda zwracająca instancję takiej dependencji musi być oznaczona annotacją `@Provides`.

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
```

Każdy moduł musi należeć do komponentu.

```kotlin
@Component(modules = [NetworkModule::class])
```