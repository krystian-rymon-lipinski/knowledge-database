**Specjalna metoda danej [[0029 Klasa|klasy]], umożliwiająca utworzenie jej instancji - obiektu tej klasy.**
W przypadku niezdefiniowania żadnego konstruktora dodany zostanie domyślny - bez parametrów. 

###### Przeciążanie konstruktorów
Można utworzyć większą liczbę konstruktorów - muszą się one jedynie różnić liczbą lub typem parametrów. 

###### Łańcuchowe wywołanie konstruktorów
Z poziomu konstruktora można wywołać:
- inny konstruktor tej klasy (przeciążony) 
- konstrukor klasy bazowej (superklasy) 

Jeżeli któraś tych instrukcji zostanie wywołana, musi być pierwszą zdefiniowaną w konstruktorze. W przypadku niewykorzystania żadnej z nich, domyślnie wywołany zostanie bezparametrowy konstruktor superklasy. 

Wykonanie konstruktorów superklasy jest konieczne, ponieważ klasa pochodna może korzystać ze składowych zdefiniowanych i zainicjalizowanych w klasie bazowej. Z tego powodu w momencie utworzenia obiektu najpierw wykonany zostanie konstruktor [[0024 Klasa podstawowa|klasy podstawowej]], następnie konstruktory kolejnych klas w hierarchii dziedziczenia, a dopiero na końcu konstruktor klasy tworzonego obiektu.

Innym sposobem na zdefiniowanie instrukcji wykonywanych w momencie tworzenia obiektu są [[002D Inicjalizator|inicjalizatory]].