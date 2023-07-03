up: [[Zasięg klas grafu]]

**W celu zapewnienia klasom kontenera odpowiedniego zasięgu, którego nie definiuje Dagger (np. dla aktywności/fragmentu) należy zdefiniować własną annotację**. Wówczas można jej używać do oznaczania zasięgu dokładnie tak, jak `@Singleton`.

```kotlin
@Scope  
@Retention(value = AnnotationRetention.RUNTIME)  
annotation class ActivityScope
...
@ActivityScope
@Component
interface SomeComponent { 
	fun inject(targetActivty: SomeActivity)
	fun inject(targetFragment: SomeFragment)
}
```

W kodzie odbywa się to poprzez zdefiniowanie we właściwym miejscu referencji do komponentu oznaczonego własną annotacją - najczęściej w klasie aktywności lub fragmentu. Później można z tej referencji korzystać we wszystkich miejscach wstrzykiwania, w których potrzebne są dependencje - oczywiście w dopóki klasa-kontener istnieje, czyli w obrębie zasięgu.

```kotlin
class SomeActivity {
	lateinit var someComponent: SomeComponent

	override fun onCreate(savedInstanceState: Bundle) {
		someComponent = DaggerSomComponent.create()
		someComponent.inject(this)
	}
}
```