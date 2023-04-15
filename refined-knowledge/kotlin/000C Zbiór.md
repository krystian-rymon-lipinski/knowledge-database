up: [[000A Kolekcje]]

**Zwraca uwagę na unikatowość przechowywanych elementów. Nie pozwala dodawać już istniejących.
Element zbioru nie ma indeksu. Nie można go po nim wyszukać.**

Dwa zbiory są sobie [[0005 Równość obiektów|równe]] ("\=="), jeśli zawierają dokładnie te same elementy - bez znaczenia na ich kolejność.

```kotlin
val s = setOf("ab", "ac", "ab") /* Rozmiar zbioru to 2. */
val presentInSet = s.contains("ac") 
/* Sprawdzenie, czy zbiór zawiera element. Zwraca boolean. */
```

###### Unikalność obiektu w zbiorze
**Klasa Set bada równość tylko tych obiektów, które mają te same [[000E Kody mieszające|kody mieszające]]!**
**Element zostanie dodany do zbioru tylko jeśli jest unikalny!**
1.  Czy zbiór zawiera już taki kod mieszający?
	nie → unikalny obiekt
	tak → 2)
2. Czy referencje wskazują na ten sam obiekt ("\=\==")?
	nie → 3) 
	tak → duplikat
3. Czy dwa obiekty są równe ("\==")? 
	nie → unikalny obiekt 
	tak → duplikat