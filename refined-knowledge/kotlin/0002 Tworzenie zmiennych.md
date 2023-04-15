up:  [[Zmienne (MOC)]]

**W Kotlinie możliwe jest [[Deklaracja, definicja, inicjalizacja|deklarowanie]] zmiennych jako tylko do odczytu bądź do odczytu i do zapisu.** Aby móc używać zmiennej w Kotlinie, musi ona zostać [[Deklaracja, definicja, inicjalizacja|zainicjalizowana]] wartością!

### read-only (**val** = value): 
```kotlin
val readOnlyValue = 0 
```
Utworzony zostaje obiekt typu Int, do którego odnosi się referencja _readOnlyValue_. Do tej referencji nie można już przypisać innego obiektu. A więc nie można nawet przypisać innej wartości (bo to również byłby nowy obiekt). Można tylko tę wartość odczytać. 

### read & write (**var** = variable): 
```kotlin
var writableVariable = 10
writableVariable = 22 /* Do referencji writableVariable można przypisać inny obiekt. */
```

###### Przykłady 
```kotlin
val someValue /* ERROR - kompilator nie ma się skąd domyślić typu.  */
var defaultNumber = 20 /* Deklaracja i inicjalizacja. Typ: Int, domyślny. */
var shortValue: Short /* Deklaracja poprawna. Typ podany jawnie. */
var byteValue: Byte = 12 /* Deklaracja i inicjalizacja. Typ podany jawnie. */
var notLetter: Char = "letter" /* ERROR - typy nie są zgodne. */
```
