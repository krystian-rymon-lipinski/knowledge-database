### Lista
**Zwraca uwagę na kolejność przechowywanych elementów.**
Dwie listy są sobie [[0005 Równość obiektów|równe]] ("\=="), jeśli zawierają dokładnie te same elementy na tych samych miejscach w liście (z tymi samymi indeksami).

Operacje na dowolnej liście:
```kotlin
val x = l.get(10) / l[10] /* Wczytanie wartości z listy. */
val l2 = l1.sorted() /* Zwrócenie nowej, posortowanej listy l2. */
val i = l.indexOf(200) /* Zwrócenie indeksu podanego elementu. */ 
/* -1, jeśli element z żądanym indeksem nie istnieje. */
```
Operacje na liście mutowalnej:
```kotlin
l.set(1, 200) / l[1] = 200 /* Zmiana wartości elementu listy. */
l1.sort() /* Sortuje listę l.
```
Próba operacji na nieistniejącym indeksie (zapisu lub odczytu) zakończy się zgłoszeniem [[0009 Wyjątki|wyjątku]] IndexOutOfBoundException.
___

#tech-area/kotlin 
[[000A Kolekcje]]