### Interfejs
**Podstawowa struktura programowania obiektowego. Nie może on opisywać stanu obiektu, definiuje jedynie jego zachowania poprzez metody** (i ewentualnie składowe w niektórych językach).

Interfejs opisuje kontrakt - co powinny móc robić obiekty będące jego typem.
Interfejs nie opisuje, jak powinny to robić. Ponieważ każdy może chcieć robić to inaczej. 

Obowiązek zdefiniowania implementacji spoczywa na konkretnym obiekcie. Wówczas to przechodzi się od abstrakcji (definicje metod w interfejsie) do konkretu (implementacje tychże metod dla konkretnej klasy).
###### Zastosowanie
Interfejs jest **implementowany** przez klasę. Musi ona wówczas przesłonić wszystkie jego abstrakcyjne metody. Obiekty takiej klasy są [[0014 Polimorfizm|polimorficzne]], można się do nich odwołać poprzez referencję o typie klasy lub interfejsu.

---
#tech-area/theory/programming-paradigms/object-oriented 