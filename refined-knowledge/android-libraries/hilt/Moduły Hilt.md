up: [[013.8 Hilt]]

**Klasy dostarczające instancje niemożliwe do utworzenia poprzez konstruktor, dokładnie tak jak w Daggerze, poprzez [[@Module]].** Zmienia się nieco sposób deklaracji - należy podać, do jakiego typu [[Komponenty Hilt|komponentu Hilt]] należy ów moduł.

```kotlin
@Module  
@InstallIn(ViewModelComponent::class)  
object HttpModule {  
    @ViewModelScoped  
    @Provides    
    fun provideHttpService() : HttpService {  
        return Retrofit.Builder()  
            .baseUrl(INFO_BASE_URL)  
            .build()  
            .create(HttpService::class.java)  
    }  
}
```
