### Tworzenie 
W Kotlinie możliwe jest deklarowanie zmiennych jako tylko do odczytu bądź do odczytu i do zapisu.
1. read-only (**val** = value): 
```kotlin
val readOnlyValue = 0 
```
Utworzony zostaje obiekt typu Int, do którego odnosi się referencja _readOnlyValue_. Do tej referencji nie można już przypisać innego obiektu. A więc nie można nawet przypisać innej wartości (bo to również byłby nowy obiekt). Można tylko tę wartość odczytać.

2. read & write (**var** = variable): 
```kotlin
var writableVariable = 10
writableVariable = 22 /* Do referencji writableVariable można przypisać inny obiekt. */
```
---
###### Przykłady 
```kotlin
val value /* ERROR - kompilator nie ma się skąd domyślić typu.  */
var defaultNumber = 20 /* Deklaracja i inicjalizacja. Typ: Int, domyślny. */
var shortValue: Short /* Deklaracja poprawna. Typ podany jawnie.  */
var byteValue: Byte = 12 /* Deklaracja i inicjalizacja. Typ podany jawnie. */
var notLetter: Char = "letter" /* ERROR - typy nie są zgodne. */
```
---
#tech-area/kotlin 
[[deklaracja a definicja a inicjalizacja]]
[[0000 (MOC) Zmienne]]