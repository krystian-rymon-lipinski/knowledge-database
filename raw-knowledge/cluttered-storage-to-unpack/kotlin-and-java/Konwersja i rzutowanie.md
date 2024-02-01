up: [[Zmienne (MOC)]]
#status/3-freezer 

### Konwersja
```kotlin
var x = 20 /* Obiekt typu Int. */
val y = x.toLong() 
```
Powstaje nowy obiekttypu _Long_, na którego wskazuje referencja _y_. Podobnie działa to dla innych typów bazowych.


### Rzutowanie

Operator '_is'_:

```kotlin
val b: Ball = Volleyball()
if (b is Volleyball) { /* Obiekt jest typu Volleyball, bo 
konstruktorem tej klasy został stworzony. */
	b.bounceSpecially() /* Niejawne rzutowanie pozwala wywołać metodę konkretnej podklasy */
}
```

Operator '_is'_ może dokonać inteligentnego rzutowania na typ, z którym jest porównywany obiekt. Robi to, jeśli jest w stanie zagwarantować, że typ obiektu, na który wskazuje referencja, nie zmieni się od jego sprawdzenia do użycia.



Operator '_as'_:

```kotlin
val b: Ball = Volleyball()
val vb = b as Volleyball
vb.bounceSpecially()
```

Obie referencje wskazują na ten sam obiekt typu Volleyball, ale pierwsza z nich udostępnia tylko metody klasy Ball, zaś druga - metody klasy Volleyball.

