up: [[020 Kotlin MOC]]

###### Zmienne [[0006 Nullable vs. non-null]]
###### Bezpiecznie wywołanie
```kotlin
if (someObject != null) {
	/* Nienajlepszy sposób upewnienia się, czy obiekt nie jest nullem. */
	/* Przy wielowątkowości wartość obiektu może się zmienić po sprawdzeniu. */
}
```
Dlatego właśnie lepiej skorzystać z **bezpiecznego wywołania**. 
```kotlin
someObject?.doSth() /* Metoda wykonana tylko jeśli obiekt nie jest nullem. */
val x = someObject?.property /* Jeśli someObject jest nullem, wartość x to też null. */
/* Jeśli nie, x jest równe property obiektu. */
someObject?.property = 10 /* Wartość przypisana tylko jeśli someObject nie jest nullem. */ 
someObject?.itsObject?.property /* Łańcuch bezpiecznych wywołań. */
```

###### Operator _?:_ (Elvis)
```kotlin
val x = b?.radius ?: -1 
val x = if (b != null) b.radius else = -1 /* Starszy odpowiednik wyrażenia powyżej. */
```
Sprawdzane jest wyrażenie po lewej. Jeśli nie jest nullem, to jest zwracane. W przeciwnym razie zwracane jest wyrażenie po prawej stronie Elvisa.

###### Operator _!!_
```kotlin
var b: Ball? = Ball() b!!.bounce() 
```
Kompilator to przepuści, ale jeśli _b_ będzie równe null, to wywali NullPointerException. 

###### Funkcja _let_ (i inne [[Funkcje wyższego rzędu]])
```kotlin
var b: Ball? = Ball()
b?.let { 
	it.bounce() 
	it.height = 3
}
```

Umożliwia wywołanie wielu operacji na obiekcie. Operator _?._ przed _let_ zapobiega wywołaniu czegokolwiek wewnątrz lambdy, jeśli b jest równy null. Dzięki temu nie trzeba sprawdzać każdego wywołania. Bardziej zwarty kod.

Dzięki temu _it_ oznacza tu **zmienną non-null** typu Ball.

