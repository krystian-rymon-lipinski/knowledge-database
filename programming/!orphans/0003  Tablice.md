### Tablice

`var arr = longArrayOf(3, 2, 1)` 
`indexValue = arr[0]`
Inicjalizacja przez metodę. Podawane są elementy tablicy. _arr_ przechowuje referencję do obiektu typu Array\<Long\>. Zmienna _indexValue_ odnosi się do obiektu typu Long w tablicy _arr_.

`val objectArray = arrayOf<Any>(Any(), Any())`
Inicjalizacja tablicy obiektów. Kompilator jest w stanie domyślić się typu i można opuścić jawne go deklarowanie poprzez <>.



`val arr2: Array<Int>(10) { i -> i }`
Inicjalizacja poprzez konstruktor. Podawana jest ilość elementów i formuła (wyrażenie lambda), wedle której mają one być utworzone. 

Referencja _arr2_ jest tylko do odczytu - nie może wskazywać na inny obiekt. Ale sam obiekt (np. elementy tablicy) jak najbardziej może ulegać zmianom!

#tech-area/kotlin 
