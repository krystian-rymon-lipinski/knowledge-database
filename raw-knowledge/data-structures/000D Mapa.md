up: [[000A Kolekcje]]

**Lista par klucz-wartość. Klucze mapy stanowią [[000C Zbiór|zbiór]].**
Operacje na dowolnej mapie:
```kotlin
val m = mapOf("BB" to 20) /* BB to klucz, 20 to wartość. */

m.containsKey("aKey") /* Sprawdzenie istnienia konkretnego klucza w mapie. */
m.containsValue("aValue") /* Sprawdzenie istnienia konkretnej wartości w mapie. */
m.get("aKey") / m["aKey"] /* Pobranie wartości skojarzonej z kluczem. */
/* Zwraca null jeśli klucza nie ma. */
m.getValue("aKey") /* Pobranie wartości skojarzonej z kluczem. */
/* Zwraca błąd, jeśli klucza nie ma. */
```
Operacje na mapie mutowalnej:
```kotlin
m.set("ABall", 2) / m["ABall"] = 2 /* Dodanie nowej pary  do mapy. */
m["ABall"] = 10 /* Nadpisanie wartości dla konkretnego klucza. */
```
