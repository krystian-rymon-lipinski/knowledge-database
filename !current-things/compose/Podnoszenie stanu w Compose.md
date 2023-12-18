up: [[Stan funkcji komponowalnych]]

**Podnoszenie stanu (_ang. state hoisting_) - przeniesienie przechowywania stanu o funkcję wyżej, by mogły z niego skorzystać wszystkie funkcje niżej w hierarchii.**

Wówczas ta pojedyncza funkcja niższa w hierarchii staje się **pozbawiona stanu**. W zamian należy w niej zdefiniować dwa parametry: aktualną wartość zmiennej oraz lambdę z reakcją, wpływającą na stan zdefiniowany wyżej w hierarchii.

```kotlin
@Compose
fun WholeLayout() {
	val numberValue = remember { mutableStateOf(0) }
	NumberDisplayed(
		currentNumber = numberValue.value
		onButtonClicked = { numberValue.value = /* Manipulacja stanem */ }
	)
}

@Compose
fun NumberDisplayed(currentNumber: Int, onButtonClicked: () -> Unit) { }
```

**Takie podejście do definiowania stanu pozwala wypełnić [[015 Android Architecture|założenie architektoniczne]] o jednostronnym przepływie danych.**

**Stan powinien powinien być trzymany na tyle wysoko w hierarchii, by mógł zostać rozpropagowany niżej do wszystkich funkcji, które z niego (lub jego elementów) korzystają.**