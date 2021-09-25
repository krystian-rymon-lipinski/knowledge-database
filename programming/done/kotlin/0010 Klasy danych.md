### Klasy danych
***Klasy definiujące dane - ułatwiają porównywanie obiektów, które je zawierają.***
```kotlin
data class Player(val name: String, val score: Float) {  } /* Definicja */
```
###### Właściwości klas danych 
-> klasa danych ***NIE MOŻE*** być abstrakcyjna ani otwarta (ani wewnętrzna ani zapieczętowana)
-> klasa danych ***MUSI*** mieć konstruktor podstawowy i przynajmniej jedną właściwość
-> klasa danych ***MOŻE*** dziedziczyć po innych klasach, implementować interfejsy i definiować funkcje

Wszystkie właściwości zdefiniowane w konstruktorze podstawowym muszą być poprzedzone słowem val lub var.
###### Automatycznie przesłaniane funkcje
- _equals()_ - porównanie typu obiektu oraz wartości jego właściwości zdefiniowanych w konstruktorze podstawowym (poprzez domyślną implementację _equals()_ dla każdej z tych klas)
- _hashCode()_ - wygenerowanie kodu mieszającego na podstawie właściwości zdefiniowanych w konstruktorze pdostawowym
- _toString()_ - napis w formie: ___Player(name=SomeName, score=2.1f)___
 
Właściwości zadeklarowane ***poza konstruktorem podstawowym*** klasy danych ***nie zostaną uwzględnione w metodach automatycznie przesłanianych oraz w metodzie _copy()_***.


###### Kopiowanie obiektu
```kotlin
val t1 = Player("Ivanchuk", 2.5f)
val t2 = t1.copy(name = "Karpov") 
/* Utworzenie obiektu poprzez skopiowanie innego i zmianę podanych wartości. */
```
###### Pobieranie wartości klas danych:
```kotlin
val name = t1.component1() /* To samo co: name = t1.name */
val score = t1.component2() /* Kolejne składowe jako componentN */
val (name, score) = t1 /* Destrukturyzacja danych. */
/* Name i score są zmiennymi, z których można korzystać. 
Wartości przypisywane są w kolejności ich zadeklarowania w klasie. */
```

---
#tech-area/kotlin 
[[0008 (MOC) Kotlin]]

