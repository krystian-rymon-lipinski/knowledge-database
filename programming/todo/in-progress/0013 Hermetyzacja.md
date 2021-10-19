### Hermetyzacja
**Zapobiega zmianie wewnętrznego stanu obiektu przez inne obiekty poprzez jego ukrycie. Tylko własne metody obiektu są uprawnione do zmiany jego stanu.**

Obiekt może definiować możliwości zmiany wewnętrzengo stanu poprzez metody dostępne dla wszystkich, wówczas jednak ma kontrolę nad proponowanymi wartościami i może je odrzucić. 

Na przykład obiekt opisujący stan piłki poprzez ciśnienie w jej wnętrzu może dać możliwość innym obiektomi ustawiania tegoż ciśnienia, ale dobrze byłoby zabezpieczyć się przez ustawieniem wartości mniejszej od zera. 
Danie dostępu bezpośrednio do stanu (zmiennej) wyklucza taką kontrolę, podczas gdy jego ukrycie i oddanie do użytku metody, daje możliwość obwarowania podanych przez zewnętrzny obiekt parametrów stosownymi warunkami.

---
#tech-area/theory/programming-paradigms/object-oriented 
[[0011 (MOC) Programowanie obiektowe (klasowe)]]