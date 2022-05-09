### Równość obiektów

###### Operator \=== (a === b)
ZAWSZE sprawdza, czy dwie zmienne wskazują na ten sam obiekt.
Dla typów bazowych jest równoważny z == .
```kotlin
val a = 10
val b = 300
println(a !== b) // true
```
	
###### Operator == (a == b)
Jeśli:
- _a_ jest nullem
Równość zachodzi tylko wtedy, gdy _b_ również ma wartość null.
- _a_ nie jest nullem
Wywoływana jest funkcja _equals()_, która DOMYŚLNIE zachowuje się jak operator === . Można ją przesłonić, by definiować własne zasady równości.
```kotlin
override fun equals(other: Any?) : Boolean { 
	if (other == null) return false /* Sprawdzenie nulla. */ 
	if (this.javaClass != other.javaClass) return false /* Sprawdzenie typów obiektów (nie typów referencji!). */ 
	other as Volleyball /* Zrzutowanie referencji na odpowiedni typ */
	return this.radius == other.radius /* Sprawdzenie wartości właściwości. */ 
}
```

---

#tech-area/kotlin 
[[0008 (MOC) Kotlin]]
