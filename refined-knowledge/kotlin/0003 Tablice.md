up: [[Zmienne (MOC)]]

***Dwie tablice są sobie [[0005 Równość obiektów|równe]] tylko po nadpisaniu metody `equals()`!***
Kotlin nie dostarcza implementacji jak w przypadku [[000A Kolekcje|kolekcji]].

Wielkość tablicy nie może ulegać zmianie.
Można modyfikować frywolnie elementy tablicy.

###### Inicjalizacja

1. Przez metodę
```kotlin
var arr = longArrayOf(3, 2, 1)
val indexValue = arr[0]
```
Podawane są elementy tablicy. _arr_ przechowuje referencję do obiektu typu Array\<Long\>. Zmienna _indexValue_ odnosi się do obiektu typu Long w tablicy _arr_.

2. Przez tryby generyczne
```kotlin
val objectArray = arrayOf<Any>(Any(), Any())
```
Kompilator jest w stanie domyślić się typu i można opuścić jawne go deklarowanie poprzez <>.

3. Przez konstruktor
```kotlin
val arr2: Array<Int>(10) { i -> i }
```
Podawana jest ilość elementów i formuła (wyrażenie lambda), wedle której mają one być utworzone. 
Referencja _arr2_ jest tylko do odczytu - nie może wskazywać na inny obiekt. Ale sam obiekt (np. elementy tablicy) jak najbardziej może ulegać zmianom!
