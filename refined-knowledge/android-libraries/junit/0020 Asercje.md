up: [[013.1 Junit MOC]]

**Metody wspomagające testowanie. Sprawdzają, czy wartości oczekiwane są równe tym rzeczywiście otrzymanym w wyniku wywołania metody.**

Wszystkie znajdują się w klasie _Assert_. Import statyczny tej klasy spowoduje, że będzie można się do nich odnosić bezpośrednio.

###### Dostępne asercje
```java
assertEquals("expectedString", "actualString") /* Również dla obiektów */
assertArrayEquals(expectedArray, actualArray)
assertNull(object)
assertNotNull(object)
assertSame(obj1, obj2) /* Sprawdzenie, czy dwie zmienne wskazują na ten sam obiekt */
assertNotSame(obj1, obj2) 
assertTrue(someBoolean)
assertFalse(anotherBoolean)
fail() /* Zawsze powoduje niepowodzenie testu */
```
W przypadku asercji z bardziej złożonymi warunkami przejścia można wykorzystać [[AssertThat|assertThat]].
