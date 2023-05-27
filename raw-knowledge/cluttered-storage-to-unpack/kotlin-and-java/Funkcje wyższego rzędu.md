#status/3-freezer 
#tech-area/kotlin 

let, also, apply, i jeszcze parę innych

also i apply zwracają obiekt, ale:
w apply można tylko ustawiać właściwości obiektu - wówczas zwracany jest obiekt z ustawionymi parametrami
w also można wykonywać dodatkowe operacje - podaje się lambdę jako argument, która coś tam robi, a zwracany jest i tak obiekt

Wywołania te można łączyć w łańcuchy - skoro zwracają one obiekt, to na tym obiekcie można wywołać kolejną funkcję globalną.

```kotlin
return someObject.apply {
	field1 = 20
	field2 = "New name"
}.also {
	checkForPredicaments(it)
}
```

