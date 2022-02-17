### Funkcje
```kotlin
fun someFunction(intValue: Int, someChar: Char) : String { /* Definicja funkcji */
	return "someString"
}
val returnedString = someFunction(10, 'b') /* Wywołanie funkcji. */
```
***Parametry do funkcji przekazywane są przez referencję! Obiekt nie jest kopiowany, każda operacja dokonywana jest na oryginale.***
Parametry funkcji definiowane są automatycznie poprzez **_val_** - nie można zmieniać ich wartości wewnątrz funkcji.
###### Funkcje przeciążone
Funkcje o tej samej nazwie, ale innych ***TYPACH PARAMETRÓW***.
```kotlin
fun add(a: Int, b: Int) : Int {} 
fun add(a: Short, b: Short) : Int {} /* Ten sam zwracany typ nie przeszkadza. */
fun add(a: Double, b: Double) : Double {} /* Kolejna funkcja przeciążona. */ 
fun add(a: Int, b: Int) : Double {} /* ERROR */
/* Zmiana typu zwracanego nie wystarczy, jeżeli typy parametrów są te same. */
```
###### Wartości domyślne parametrów funkcji
```kotlin
fun findPlayer(name: String, isMaster: Boolean = false) {} /* Definicja */
..
findPlayer("Robinson") /* Parametr isMaster ma domyślnie wartość false. */
findPlayer("Cruzoe", true) /* Podanie konkretnej wartości parametru domyślnego. */
findPlayer(isMaster = true, name = "someName") 
/* Podanie parametrów po nazwie, kolejność nieistotna. */
findPlayer(isMaster = true) /* ERROR - nie podano wartości parametru name! */
/* A nie ma on również podanej wartości domyślnej. */
```
Nie można mieszać argumentów podanych w kolejności i z nazwy! 
(Chyba że akurat zgadzają się typy.) 
###### Funkcja main
Wywoływana jako główna funkcja programu. Nie może być wewnątrz klasy, powinna być w osobnym pliku (albo oznaczona jako @JVMStatic w companion object klasy).
```kotlin
fun main() {}
```
###### Funkcja jednoliniowa
```kotlin
/* Kompilator domyśla się typu wartości zwracanej. Klamry niepotrzebne. */ 
fun doublingFunction(number: Int) = number*2 // Tutaj Int. 
fun filtFunct(number: Int) = number > 20 // Tutaj Boolean.
```
___

#tech-area/kotlin 
[[0008 (MOC) Kotlin]]