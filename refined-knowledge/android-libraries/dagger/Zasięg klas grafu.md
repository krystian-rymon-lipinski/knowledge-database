up: [[013.7 Dagger]]
#status/0-revision-needed

**Ponieważ różne miejsca aplikacji mogą korzystać z tych samych zależności, należy zadeklarować, czy wstrzykiwanie ich powinno generować za każdym razem nową instancję, czy może korzystać z już istniejącej.** Na przykład ponowne tworzenie obiektu serwisu Retrofit lub bazy danych może być niepotrzebne i czasochłonne.

Wybór ten jest realizowany poprzez annotacje zasięgu. Jedyną definiowaną przez Dagger jest `@Singleton`, który sprawia, że utworzona raz instancja będzie zwracana dla każdego wstrzykiwania przez cały czas życia aplikacji. W celu utworzenia innych zasięgów (np. powiązania obiektów z aktywnością bądź fragmentem) należy utworzyć [[Własne annotacje zasięgu|własne annotacje zasięgu]].

> [!NOTE]
> 1. Zasięg komponentu a zasięg dependencji, które tworzy.
> 2. Czas życia komponentu a czas życia dependencji, które tworzy.
> 3. Zasięg a czas życia ogólnie - jak działa i po co?
> 
> Komponent żyje tak długo, jak długo istnieje referencja do niego. Jego zależności żyją tak długo, jak on sam. Chyba?
> 
> Czas życia i zasięg komponentu to dwie odrębne rzeczy. Brak zdefiniowania zasięgu spowoduje tworzenie nowych instancji klas dostarczanych przez komponent za każdym razem, gdy inna klasa zadeklaruje konieczność ich wstrzyknięcia. Jednakże każda z tych instancji będzie miała taki sam czas życia jak klasa, do której te zależności są dostarczane. 
> 
> Określenie zasięgu komponentu (co wymusza określenie również zasięgu jego klas) spowoduje zwracanie tych samych instancji na całym zasięgu. Może on być większy niż czas życia klasy, która zadeklarowała wstrzykiwanie tych instancji po raz pierwszy - właśnie po to, by dokładnie tę samą instancję otrzymały wszystkie inne klasy wstrzykujące tę samą zależność później. 
> 
> Najczęściej zasięg przydatny jest dla zależności definiujących wewnętrzny stan, z którego korzysta więcej niż jeden odbiorca - na przykład ViewModel dla aktywności i kilku różnych fragmentów.

Annotacją należy oznaczyć klasę której dotyczy zasięg lub metodę modułu, która generuje instancję. **Ponadto komponent musi zostać oznaczony tym samym zasięgiem jak typy klas, które zawiera oraz moduły, z których korzysta.**

```kotlin
@Singleton
@Component(modules = [AppModule::class])
interface AppComponent {
	fun inject(target: SomeActivity)
}
...
@Singleton
class Repository @Inject constructor() { }
...
class AppModule {
	@Provides
	@Singleton
	fun provideService() : RetrofitService
}
```
