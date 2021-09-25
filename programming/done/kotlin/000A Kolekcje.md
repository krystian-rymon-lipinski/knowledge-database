###### Zmienne vs niezmienne

→ Mutable - pozwala zmieniać wartości elementów oraz wykonywać operacje na kolekcji (sortowanie, kopiowanie, usuwanie, itp.)
 → Immutable - po zainicjowaniu nie można dodawać/usuwać elementów ani zmieniać wartości już istniejących
 ```kotlin
 val mutableList = mutableListOf(20, null, 30) /* List<Int?> */
 val immutableSet = setOf("firstName", "lastName") /* Set<String> */
 ```
 
###### Kolekcje vs [[0003 Tablice|tablice]]

_Wielkość struktury:_
- tablica: zawsze niezmienna
- kolekcja: zmienna jeśli tak zadeklarowano

_Elementy struktury:_
- tablica: zawsze edytowalne
- kolekcja: edytowalne jeśli tak zadeklarowano

###### Typy kolekcji:
- [[000B Lista|lista]]
- [[000C Zbiór|zbiór]]
- [[000D Mapa|mapa]]

###### Zamiany kolekcji
```kotlin
/* Skopiowanie wartości do innej struktury. */ 

val aList = setOf(3, 20).toList() /* Lub toMutableList() */ 
val aList2 = arrayOf(2, 1).toList() /* Lub toMutableList() */ 
val aSet = listOf(10, 2).toSet() /* Lub toMutableSet() */ 
val aSet2 = arrayOf(4, 3).toSet() /* Lub toMutableSet() */ 
val array = listOf(7, 1).toTypedArray() /* Typ Array<Int> */ 
val array2 = setOf(9, 4).toTypedArray() /* Typ Array<Int> */
```
___

#tech-area/kotlin 
[[0008 (MOC) Kotlin]]








