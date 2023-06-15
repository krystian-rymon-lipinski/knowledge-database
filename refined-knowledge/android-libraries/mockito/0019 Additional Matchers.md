up: [[0018 Argument Matcher]]

**Klasa AdditionalMatchers dostarcza metody definiujące dodatkowe warunki dla ArgumentMatchers, jeśli podstawowe nie wystarczają.** Wśród nich:
- funkcje logiczne: _not()_, _and()_, _or()_
- równości (nie)ostre: _geq()_, _leq()_, _gt()_, _lt()_ 
- string zawierający łańcuch (regex): _find()_ 
- równość Comparable i tablic: _cmpEq()_, _aryEq()_ 
- wartość +/- delta: _eq()_

Pełna lista metod dostępna jest [tu](https://www.javadoc.io/doc/org.mockito/mockito-core/2.2.7/org/mockito/AdditionalMatchers.html).

