up: [[013.2 Mockito MOC]]

**Konfiguracja mocka, by zachował się w określony sposób, gdy zostanie wywołana na nim metoda**. Dokonywana poprzez zdefiniowanie zwracanych wartości dla określonych parametrów poprzez konstrukcję ***when-then***.

###### Przykłady użycia
```java
CustomList listMock = Mockito.mock(CustomList.class)

when(listMock.add(-1)).thenReturn(false);
when(listMock.add(anyInt())).thenReturn(false); /* 'false' dla dowolnego parametru. */
doReturn(false).when(listMock).add(anyInt()) /* Alternatywa dla linii powyżej. */

when(listMock.add(anyString())).thenThrow(IllegalStateException.class);
when(listMock.size()).thenCallRealMethod();
```
Aby zdefiniować własne zachowania, można użyć [[ThenAnswer|thenAnswer]].

###### Mock vs. Spy
Stubbingu mocka można dokonać na dwa sposoby, zarówno _when-then_, jak i _doReturn-when_ zadziałają poprawnie.
Stubbingu spy'a można dokonać tylko poprzez _doReturn-when_.

###### Wywołania wielokrotne
Można zdefiniować różne zachowania mocka, w zależności od tego, który raz zostanie wywołana na nim metoda.
```java
when(listMock.add(anyString())) 
.thenReturn(false) /* Zwrócenie 'false' podczas pierwszego wywołania */
.thenThrow(IllegalStateException.class); /* Zgłoszenie błędu podczas drugiego */
```
Każde kolejne wywołanie wygeneruje zachowanie, które zostało zdefiniowane jako ostatnie.