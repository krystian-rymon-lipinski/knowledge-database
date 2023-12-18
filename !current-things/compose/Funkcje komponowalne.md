up: [[Jetpack Compose]]

**Funkcje komponowalne _(ang. composable functions)_ - funkcje generujące komponenty UI. Składają się na kompozycję, która jest wizualną reprezentacją aktualnego stanu aplikacji.** Kompozycja jest opisywana strukturą drzewa.

Należy je oznaczać annotacją `@Composable`, a wywoływać można tylko z innych funkcji komponowalnych. Aby wywołać pierwszą (główną), należy wykorzystać funkcję `setContent { }`, która przyjmuje funkcję komponowalną za parametr.

Funkcja `setContent { }` wymaga dependencji:

```kotlin
implementation("androidx.activity:activity-compose:1.7.2")
```

```kotlin
override fun onCreate(savedInstance: Bundle?) {
	setContent {
		MainComposableFunction() 
	}
}

@Composable
fun MainComposableFunction() { /* Possibly other composables */ }
```


Mogą zostać wywołane w dowolnej kolejności, równolegle, zostać pominięte lub być wywoływane bardzo często (np. dla każdej klatki animacji). **Nie należy polegać na kolejności ich wykonywania.**

Są rekomponowane (wywoływane ponownie), gdy zmieni się wartość ich parametru lub wewnętrzny stan.
Android Studio posiada [[Narzędzia Android Studio|narzędzie]] Layout Inspector - można w nim podglądnąć liczbę rekompozycji, którym podlegają konkretne jego elementy.
