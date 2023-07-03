#status/2-backlog 

**Zasady programowania obiektowego.**

**S - Single Responsibility** - only one reason to modify class
**O - Open/Closed** - open for extensions, closed for modifications
**L -  Liskov Substitution** - functions using references to base classes need to be able to use derived ones as well (polymorphism)
**I - Interface Segregation** - many deidacted interfaces are better than one general one
**D - Dependency Inversion** - high-level modules should not depend on low-level ones; dependencies should be based on abstractions;
Wyższy moduł nie zależy od niższego - zarówno wyższy i niższy zależą od abstrakcji.
Jeżeli na przykład ViewModel chce korzystać z repozytorium, to powinien zależeć tylko od interfejsu definiującego akcje na repozytorium, które to repozytorium implementuje.