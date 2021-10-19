### Argument Matcher
**Wykorzystywany przy [[001D Stubbing|stubbingu]], wywołaniu i [[001E Weryfikacja|weryfikacji]] Mocków. Służy do narzucenia warunków na argumenty metody, zamiast spodziewania się konkretnych wartości. ** Nie może być wartością zwracaną ani zmienną.
###### Przykład

```java
class Address {
	String city;
	int code
	public String concatAddress(String city, int code) { ... }
}
..
@Mock Address ad;

when(ad.concatName(anyString(), anyInt()).thenReturn("a1"); 
/* Stubbing. Wywołanie metody na mocku ZAWSZE zwróci a1. */
stubbedResult = ad.concatString(anyString(), anyInt()); /* Np. tutaj. */

verify(ad).concatAddress(anyString(), anyInt());
/* Weryfikacja, czy metoda została wywołana (z jakimikolwiek argumentami). */
```

***Jeśli choć jeden argument metody jest Argument Matcherem, reszta również musi! Jako any() lub jako eq().***

###### _any()_ vs. _eq()_
Dowolne wartości (lub obiekty) kontra konkretne wartości.

```java
verify(ad).concatName(anyString(), eq(30));
/* Weryfikacja przechodzi dla dowolnego Stringa i konkretnej wartości int. */
```

Bardziej złożone warunki na Argument Matchers można definiować poprzez [[0019 Additional Matchers|AdditionalMatchers]] lub zdefiniowanie [[001A Custom Matcher|własnego matchera]].


---
#tech-area/testing/unit-testing/mockito 