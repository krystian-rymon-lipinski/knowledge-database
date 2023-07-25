up: [[0056 Model-View-ViewModel]]
#status/0-revision-needed 

**Służy do przechowywania stanu wyświetlanego w elementach UI.**
**To w nim dokonuje się konwersja z klasy danych modelu na klasę danych stanu widoku** (np. tak jak [tu](https://ryanharter.com/blog/2019/07/encapsulating-view-state/) lub [tu](https://proandroiddev.com/supercharge-android-mvvm-part-1-viewstate-and-actionstate-5816500580ed)). Wynika to z tego, że widok nie musi wiedzieć o całym modelu, potrzebuje tylko tych danych, które wyświetla. ViewModel jest właśnie tym miejscem, gdzie powinno się to zrobić.

**Utworzenie własnego ViewModelu wymaga dziedziczenia po klasie ViewModel.**

Przypisanie go do zmiennej odbywa się przy wykorzystaniu klasy **ViewModelProvider**. 
__this__ oznacza tu klasę implementującą interfejs **LifecycleOwner** - implementują go wszystkie klasy aktywności, fragmentów i dialogów.
```kotlin
val viewModel = ViewModelProvider(this).get(CustomViewModel::class.java)
```

Można utworzyć własny ViewModel z parametrami - w tym celu trzeba utworzyć klasę implementującą interfejs **ViewModelProvider.Factory** i zapewnić implementację metody create(). Wówczas ta klasa jest drugim argumentem ViewModelProvidera.

```kotlin
class CustomViewModel(arg: Int) : ViewModel() {
	class Factory(private val arg: Int) : ViewModelProvider.Factory {  
	    override fun <T : ViewModel> create(modelClass: Class<T>): T {  
	        return CustomViewModel(arg) as T  
	    }  
	}
}
...
val viewModel = ViewModelProvider(this, CustomViewModel.Factory(this))  
			    .get(CustomViewModel::class.java)
```

ViewModel jest związany z obiektem typu **LifecycleOwner**, dopóki ten nie zostanie zniszczony. Jeżeli taki obiekt poprosi kolejny raz o ViewModel, zwrócona zostanie instancja już istniejąca i z nim powiązana.

Specjalną odmianą ViewModelu jest **AndroidViewModel**, który jako argument przyjmuje klasę **Application** - pozwala to operować na kontekście aplikacji wewnątrz tego ViewModelu.

**ViewModel pozostaje w pamięci, dopóki istnieje obiekt, z którym jest związany.**
Dla [[Activities|Aktywności]] - dopóki nie zostanie zakończona (wywołane *onDestroy()*).
Dla [[Fragments|Fragmentu]] - dopóki nie zostanie odpięty (wywołane *onDetached()*).

---

"The `ViewModel` is scoped to the navigation graph." Jak działa to w ujęciu TaskStacka?

Info [stąd](https://developer.android.com/topic/architecture/ui-layer/stateholders):
- Integration with [Navigation](https://developer.android.com/jetpack/compose/navigation):
    - Navigation caches ViewModels while the screen is on the back stack. This is important to have your previously loaded data instantly available when you return to your destination. This is something more difficult to do with a state holder that follows the lifecycle of the composable screen.
    - The ViewModel is also cleared when the destination is popped off the back stack, ensuring that your state is automatically cleaned up. This is different from listening for the composable disposal that can happen for multiple reasons such as going to a new screen, due to a configuration change, or other reasons.

---

https://ryanharter.com/blog/2019/07/encapsulating-view-state/
https://proandroiddev.com/supercharge-android-mvvm-part-1-viewstate-and-actionstate-5816500580ed
https://proandroiddev.com/livedata-with-single-events-2395dea972a8


