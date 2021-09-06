### Tworzenie 
W Kotlinie możliwe jest deklarowanie zmiennych jako tylko do odczytu bądź do odczytu i do zapisu.
1. read-only: 
`val readOnlyVariable = 0`
Utworzony zostaje obiekt typu Int, do którego odnosi się referencja _readOnlyVariable_. Do tej referencji nie można już przypisać innego obiektu. A więc nie można nawet przypisać innej wartości (bo to również byłby nowy obiekt). Można tylko tę wartość odczytać.

2. read & write: 
`var writableVariable = 10`
`writableVariable = 22`
Do referencji _writableVariable_ można przypisać inny obiekt. 
___

### Przykłady 
`val value` **ERROR** - kompilator nie ma się skąd domyślić typu. 
`var defaultNumber = 20` Deklaracja i inicjalizacja. Typ: Int, domyślny.
`var shortValue: Short` Deklaracja poprawna. Typ podany jawnie. 
`var byteValue: Byte = 12`  Deklaracja i inicjalizacja. Typ podany jawnie. 
`var notLetter: Char = "letter"` **ERROR** - typy nie są zgodne.
___

#tech-area/kotlin 
[[deklaracja a definicja a inicjalizacja]]