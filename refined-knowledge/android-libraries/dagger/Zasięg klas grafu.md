up: [[013.7 Dagger]]

**Ponieważ różne miejsca aplikacji mogą korzystać z tych samych zależności, należy zadeklarować, czy wstrzykiwanie ich powinno generować za każdym razem nową instancję, czy może korzystać z już istniejącej.** Na przykład ponowne tworzenie obiektu serwisu Retrofit lub bazy danych może być niepotrzebne i czasochłonne.

Wybór ten jest realizowany poprzez annotacje zasięgu. Jedyną definiowaną przez Dagger jest `@Singleton`, który sprawia, że utworzona raz instancja będzie zwracana dla każdego wstrzykiwania przez cały czas życia aplikacji. W celu utworzenia innych zasięgów (np. powiązania obiektów z aktywnością bądź fragmentem) należy utworzyć [[Własne annotacje zasięgu|własne annotacje zasięgu]].

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

Przy braku zdefiniowania zasięgu kontener (i jego obiekty) żyją tak długo, jak obiekt klasy, w której został zadeklarowany i giną wraz z nim. Jednakże każde kolejne wstrzykiwanie będzie generowało nową instancję zależności. Na przykład bez zdefiniowanych zasięgów wstrzyknięcie ViewModelu dla fragmentu po zrobieniu tego dla aktywności wygeneruje osobne instancje zamiast skorzystania z tej samej.
