up: [[Zmienne (MOC)]]
#status/freezer 

### Konwersja
```kotlin
var x = 20 /* Obiekt typu Int. */
val y = x.toLong() 
```
Powstaje nowy obiekttypu _Long_, na którego wskazuje referencja _y_. Podobnie działa to dla innych typów bazowych.


### Rzutowanie

ClassCastException - niepowodzenie rzutowania:

```kotlin
val vb = b as Volleyball /* Jeżeli w b zapisany jest już      obiekt typu innego niż Ball, nie uda się zrzutować i program się wysypie. */
val vb = b as? Volleyball /* Bezpieczne rzutowanie. Zwraca    null, jeśli się nie powiedzie. */ 
```


as
as?
is
is?

