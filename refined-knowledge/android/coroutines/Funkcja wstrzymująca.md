up: [[Korutyna]]

**Funkcja wstrzymująca (_ang. suspending function)_ to funkcja, która może zostać zatrzymana i wznowiona później bez utraty swojego stanu oraz zmiennych, na których operuje.** Umożliwia to nie-blokowanie innych wątków (w tym wątku głównego), co jest wykorzystywane podczas przeprowadzania czasochłonnych operacji.

Jest oznaczona słowem kluczowym `suspend` i musi zostać wywołana wewnątrz korutyny. Wstrzymuje ona dalsze sekwencje kodu wewnątrz korutyny do momentu zakończenia działania metody.

```kotlin
someCoroutineScope.launch {
	someMethod()
	someOtherWork() /* Wykona się dopiero, gdy someMethod() się zakończy */
}
...
suspend fun someMethod() {
	/* */
}
```