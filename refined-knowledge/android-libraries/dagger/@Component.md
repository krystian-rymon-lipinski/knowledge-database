up: [[013.7 Dagger]]

**Oznaczenie interfejsu generującego podczas kompilacji klasę-kontener - jest ona w stanie tworzyć instancje klas należących do grafu zależności.**

Można zdefiniować dodatkowe metody, które będzie posiadał kontener, możliwych do wywołania z poziomu kodu.

```kotlin
@Component
interface RepositoryComponent {
	fun createRepository() : SomeRepository /* Zwrócenie instancji klasy z kontenera */
	fun inject(target: SomeActivity) /* Wstrzyknięcie zależności z kontenera do klasy */
}
```