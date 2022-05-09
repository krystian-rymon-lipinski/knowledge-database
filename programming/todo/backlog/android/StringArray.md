Definiowanie łańcuchów w tablicy, które można później wywołać jak zwykły resource.

Sensowny tylko dla stałych wartości!
Dla wartości dynamicznych lepiej to zrobić w kodzie!

Wybranie napisu o indeksie 0 w tablicy.
Trzeba przez resources.
```kotlin
context.resources.getStringArray(R.array.device_types)[0] 
```