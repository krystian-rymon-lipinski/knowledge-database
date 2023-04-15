up: [[Zmienne (MOC)]]

###### Liczby stałoprzecinkowe
Domyślna wartość = 0.
```kotlin
val intValue = 32 /* Typ Int. Domyślny dla wszystkich liczb całkowitych. 32 bity. */
var longValue = 64L /* Typ Long. Trzeba go jawnie podać. 64 bity. */
var shortValue: Short = 10 /* Typ Short. Trzeba go jawnie podać. 16 bitów. */
var byteValue: Byte = 10 /* Typ Byte. Trzeba go jawnie podać. 8 bitów. */
val binaryValue = 0b1111_1000 /* Liczba zapisana binarnie. Domyślnie Int. _ jest bezkarne. */
var hexValue = 0xF3_AA /* Liczba zapisana szesnastkowo. Domyślnie Int. _ jest bezkarne. */
```

###### Liczby zmiennoprzecinkowe
Domyślna wartość = 0.0.
```kotlin
var doubleValue = 8.5 /* Typ Double. Domyślny dla liczb z przecinkiem. 64 bity. */
val floatValue = 8.5f /* Typ Float. Trzeba go jawnie podać. 32 bity. */
```

###### Inne 
```kotlin
var booleanValue = true /* Typ Boolean. Domyślna wartość = false */
val charValue = 'A' /* Typ Char. Domyślna wartość = \u0000. */
var stringValue = "Something" /* Typ String. Domyślna wartość nie istnieje. */
```

Domyślna wartość typu Char to de facto liczba, która definiuje znak. Lista kodowań wszystkich używanych znaków to [[tablica ASCII]].