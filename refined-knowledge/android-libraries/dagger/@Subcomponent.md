up: [[013.7 Dagger]]

**Oznaczenie komponentu, który rozszerza inny komponent. Najczęściej po to, by móc korzystać z zależności zdefiniowanych w rodzicu na szerszym [[Zasięg klas grafu|zasięgu]], dodatkowo definiując własne dependencje na zasięgu mniejszym. Subkomponent nie może definiować takiego samego zasięgu jak jego rodzic.**

Aby móc skorzystać z subkomponentu, należy:
1. Zdefiniować subkomponent oraz dodać fabrykę generującą jego instancje
2. Zdefiniować moduł opisujący subkomponent
3. Dodać moduł subkomponentu do komponentu-rodzica oraz metodę zwracającą fabrykę subkomponentu
4. Wygenerować referencję subkomponentu w kodzie dokonującym wstrzykiwania

```kotlin
@Subcomponent 
interface SmallerComponent { 
	@Subcomponent.Factory
	interface Factory {
		fun create(): SmallerComponent
	}
}
...
@Module(subcomponents = SmallerComponent::class)  
class SubcomponentsModule { ... }
...
@Component(modules = [SubcomponentsModule::class])
interface MainComponent { 
	fun smallerComponent() : SmallerComponent.Factory
}
...
/* Założenie: mainComponent ma zasięg aplikacji i jest definiowany w klasie MyApplication rozszerzającą klasę Application */
val smallerComponent = (applicationContext as MyApplication)
	.mainComponent.smallerComponent.create()
smallerComponent.inject(target) // wstrzykiwanie zależności subkomponentu
```