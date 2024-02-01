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


---

Metody operujące na kolekcjach.

```kotlin
val array = arrayOf(Volleyball(), Handball())
val biggestBall = array.maxBy { it.radius } /* Znalezienie obiektu największego ze względu na podane kryterium. */
val cheapestBall = array.minBy { it.price } /* Znalezienie obiektu najmniejszego ze względu na podane kryterium. */
/* maxBy i minBy na pustej kolekcji zwróci null */
val sumOfRadiuses = array.sumBy { it.radius } /* Zwraca sumę wartości padanego parametru wszystkich elementów kolekcji. */
val sumOfOtherThings = array.sumByDouble { it.diameter } /* To samo co wyżej, ale lambda zwraca double. */

val sortedBalls = array.filter { it.weight > 0.5 } /* Przefiltrowanie listy ze względu na kryterium. */
/* Istnieje mnóstwo różnych funkcji filter. */

val modifiedBalls = array.map { /* */ }   /* Przekształcenie każdego elementu listy w sposób określony w lambdzie. */
/* Funkcja map zwraca listę! Istnieje mnóstwo różnych funkcji map. */

array.forEach { println(it.radius) } /* forEach działa jak pętla */

val map = array.groupBy { it.name } /* Pogrupowanie elementów listy; zwraca mapę, gdzie klucze to kategorie grupowania, a wartości to listy, które zawierają obiekty pasujące do kategorii-kluczy */

val someSum = arrayOf(1, 2, 3).fold(0) { currentSum, arrayItem -> currentSum + arrayItem } /* Pierwszy argument, to wartość początkowa, na rzecz której wykonane zostaną operacje dla każdego elementu listy, a wynik każdej kolejnej operacji zapisany w wartości (już nie tak) początkowej. CurrentSum jest typu zadeklarowanego jako pierwszy argument funkcji fold. */
val anotherSum = arrayOf(1, 2, 3).reduce { currentSum, arrayItem -> currentSum + arrayItem } /* To samo co wyżej, tylko pierwszy element listy jest brany jako wartość początkowa i już nie traktowany jako element kolekcji. */
/* Domyślnie od lewej do prawej, foldRight() i reduceRight() odwracają kolejność (dla List, Sety i Mapy nie mają kolejności... */
```

Tego typu wywołania można łączyć w łańcuchy:

```kotlin
val arrayInts = arrayOf(1, 2, 3, 4)
val sortedAndDoubled = arrayInts.filter{ it > 2 }.map{ it * 2 } /* filter zwraca nową kolekcję, na której zostaje wykonana metoda map*/
```

Lambdy mają dostęp do zmiennych zdefiniowanych poza swoim zasięgiem - nazywane są one 
_domknięciem_ lambdy.

```kotlin
var number = 20
val arrayInts = arrayOf(1, 3)
arrayInts.forEach { number+=it } /* number = 24 */
```

