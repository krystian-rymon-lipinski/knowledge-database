### Wyjątki
Wyjątek to obiekt klasy Exception - można definiować swoje, które tę klasę rozszerzają.

Kotlin nie rozróżnia wyjątków sprawdzanych i niesprawdzanych - nie trzeba deklarować, że metoda zgłasza wyjątek. A nawet nie można tego zrobić - przynajmniej nie w sygnaturze metody.
Jedyną opcją zasygnalizowania (na potrzeby Javy), że metoda może zgłosić wyjątek, jest umieszczenie [[Annotacje|annotacji]] @Throws.
```kotlin
@Throws(NotEnoughPlayersException::class)
fun playMatch(numberOfPlayers: Int) {
	if (numberOfPlayers < 12) throw NotEnoughPlayersExeption() /* Zgłoszenie wyjątku. */
}
```
```kotlin
try {
	x.playMatch(10)
} catch (e: NotEnoughPlayersException) { /* Obsłużenie wyjątku. */
/* Wykonywane, gdy w bloku try coś się nie uda. */ 
} finally { /* Wykonywane ZAWSZE po bloku try/catch, niezależnie od ścieżki. */ }
```
###### Wyjątki w wyrażeniach 
```kotlin
val result = try { someNumber.returnValue() } catch (err: Exception) { null } 
```
_result_ jest typu Int?, ponieważ tylko on pokrywa oba typy, które wyrażenie może zwrócić. 
```
val number = b?.radius ?: throw BallRadiusNotExisting()
```
_number_ jest typu Int, ponieważ komenda _throw_ kończy program lub powoduje przeskok do _catch_ - nie trzeba zapisywać wyniku wyrażenia.

Throw ma typ *Nothing* i nie przyjmuje on żadnej wartości. *Nothing?* może mieć tylko wartość null. Przydaje się do oznaczania miejsc w kodzie, do których nigdy nie będzie można dotrzeć.
```kotlin
fun fail(): Nothing { /* To tylko oznaczenie, nic innego nie daje. */
	throw CustomException()
}
```

---

#tech-area/kotlin 
[[0008 (MOC) Kotlin]]