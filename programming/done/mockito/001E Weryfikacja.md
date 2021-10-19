
### Weryfikacja
**Sprawdzenie, czy mock podlegał  interakcjom podczas testowego wywołania metody na obiekcie.** Możliwe jest skontrolowanie samego faktu wywołania metody, jak również 

###### Przykłady
```java
CustomList mockedList = Mockito.mock(CustomList.class);

verify(mockedList).size(); /* Przejdzie dla wywołania metody size() na mocku */
verify(mockedList, only()).size() /* Przejdzie dla wywołania tylko tej metody */
verify(mockedList, times(1)).size() /* Przejdzie dla dokładnie jednego wywołania */
verify(mockedList, never()).size() 
verify(mockedList, atLeast(1)).size()
verify(mockedList, atMost(5)).size()

verify(mockedList).add("arg") /* Przejdzie dla wywołania z dokładnie tym parameterem */
verify(mockedList).add(anyString()) /* Przejdzie dla wywołania z dowolnym parametrem */

verifyZeroInteractions(mockedList)
verifyNoMoreInteractions(mockedList)
```
Dodatkowe warunki na parametry można definiować poprzez [[0018 Argument Matcher|ArgumentMatchers]] oraz [[0016 Argument Captor|ArgumentCaptors]].
Kolejność interakcji można sprawdzać przy pomocy [[001F InOrder]].

---

#tech-area/testing/unit-testing/mockito 
[[0017 (MOC) Mockito]]