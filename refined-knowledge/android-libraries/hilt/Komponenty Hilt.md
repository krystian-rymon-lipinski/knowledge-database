 up: [[013.8 Hilt]]

**Są to komponenty Dagger, których nie trzeba definiować w kodzie - wystarczy oznaczyć klasę, z którą ma zostać powiązany komponent poprzez annotację `@AndroidEntryPoint`.**

```kotlin
/* Zostanie utworzony komponent powiązany czasem życia z aktywnością */
@AndroidEntryPoint  
class MainActivity : AppCompatActivity() { }
```

Klasy oznaczane tą annotacją to miejsca wstrzykiwania, początki grafu zależności. Każda z nich definiuje konkretny typ komponentu oraz annotację zasięgu.

- `Application` -  `SingletonComponent` - `@Singleton`
- `Activity` - `ActivityComponent` - `@ActivityScoped`
- `Fragment` - `FragmentComponent` - `@FragmentScoped`
- `ViewModel` - `ViewModelComponent` - `@ViewModelScoped`
- `View` - `ViewComponent` - `@ViewScoped`
- `Service` - `ServiceComponent` - `@ServiceScoped`

**Fragmenty Hilt muszą być podpięte pod aktywność oznaczoną jako `@AndroidEntryPoint`!

Tworzenie i niszczenie instancji komponentu (oraz klas-zależności, które wygenerował) wykonuje automatycznie Hilt i jest ono powiązane z metodami `onCreate()` i `onDestroy()` klasy Androida, której dotyczy komponent.

Domyślnie dependencje w Hilcie nie definiują zasięgu, co sprawia, że zostanie wygenerowana nowa jej instancja za każdym razem, gdy jakaś klasa zadeklaruje potrzebę jej wstrzyknięcia. Aby to zmienić, należy oznaczyć klasę (lub moduł) annotacją dokładnie w taki sam sposób jak w Daggerze.