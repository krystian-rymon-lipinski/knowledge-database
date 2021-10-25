### Tablice

***Dwie tablice są sobie [[0005 Równość obiektów|równe]] tylko po nadpisaniu metody _equals()_!***
Kotlin nie dostarcza implementacji jak w przypadku [[000A Kolekcje|kolekcji]].

Wielkość tablicy nie może ulegać zmianie.
Można modyfikować frywolnie elementy tablicy.

###### Inicjalizacja
```kotlin
var arr = longArrayOf(3, 2, 1)
indexValue = arr[0]
```
Inicjalizacja przez metodę. Podawane są elementy tablicy. _arr_ przechowuje referencję do obiektu typu Array\<Long\>. Zmienna _indexValue_ odnosi się do obiektu typu Long w tablicy _arr_.

```kotlin
val objectArray = arrayOf<Any>(Any(), Any())
```
Inicjalizacja tablicy obiektów. Kompilator jest w stanie domyślić się typu i można opuścić jawne go deklarowanie poprzez <>.

```kotlin
val arr2: Array<Int>(10) { i -> i }
```
Inicjalizacja poprzez konstruktor. Podawana jest ilość elementów i formuła (wyrażenie lambda), wedle której mają one być utworzone. 

Referencja _arr2_ jest tylko do odczytu - nie może wskazywać na inny obiekt. Ale sam obiekt (np. elementy tablicy) jak najbardziej może ulegać zmianom!
___


#tech-area/kotlin 
[[0000 (MOC) Zmienne]]