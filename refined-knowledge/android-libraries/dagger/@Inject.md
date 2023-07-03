up: [[013.7 Dagger]]

**Oznaczenie miejsc, w których Dagger ma dokonać wstrzykiwania zależności. Można to zrobić poprzez konstruktor, pole lub metodę.**

**Każda klasa, która ma zostać wstrzyknięta, musi posiadać dokładnie jeden konstruktor również oznaczony tą annotacją (nieoznaczonych może mieć więcej). W ten sposób Dagger wie, z jakimi dokładnie parametrami utworzyć instancję klasy.** Wówczas będzie ona mogła zostać dodana do klasy-kontenera, stając się elementem grafu zależności.

```kotlin
class CustomViewModel : ViewModel() {
	@Inject lateinit var repository: Repository /* Oznaczenie miejsca wstrzykiwania */
	lateinit var otherRepository: OtherRepository

	@Inject /* Oznaczenie miejsca wstrzykiwania */
	fun setDependencies(repository: OtherRepository) {
		otherRepository = repository
	}
}
...
class Repository @Inject constructor() {} /* Oznaczenie konstruktora, by zdefiniować parametry wstrzykiwanej klasy (tu: żadne) */
...
class OtherRepository @Inject constructor(private val SomeDependency) {}
/* Oznaczenie konstruktora, by zdefiniować parametry wstrzykiwanej klasy.
Ale również oznaczenie miejsca wstrzykiwania, klasa SomeDependency będzie musiała zdefiniować konstruktor oznaczony annotacją @Inject */
```

Pola do których wstrzykiwane są zależności nie mogą być prywatne (muszą być przynajmniej package-private). Wstrzykiwanie przez metodę dokonywane jest przez Dagger zaraz po skonstruowaniu obiektu. Metody oznaczone jako `@Injected` nie powinny być wywoływane z poziomu kodu, a ich parametrami powinny być klasy należące do grafu zależności.