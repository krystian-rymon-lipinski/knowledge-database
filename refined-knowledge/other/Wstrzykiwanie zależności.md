up: [[013 Android Libraries MOC]]
#android/app-architecture

**Dostarczanie klasie A obiektów klas, od których zależy, poprzez parametry (konstruktora lub metod) zamiast tworzenia instancji tych obiektów wewnątrz samej klasy A.** Pozwala to dostarczać różne typy obiektu (które mogą definiować swoje implementacje zachowań) oraz zastępowanie obiektu [[001B Mock|mockiem]] na potrzeby testów.

W większej skali, wykorzystując [[015 Android Architecture|rekomendowaną architekturę]] aplikacji, gdzie zależności mają swoje zależności, dobrze jest zamodelować [[Graf aplikacji|graf aplikacji]].

Manualne wstrzykiwanie zależności może stawać się trudniejsze w miarę rozwoju aplikacji, można więc skorzystać z bibliotek, które robią do automatycznie.
- podczas czasu działania aplikacji _(ang. runtime)_ - może powodować problemy, lepiej nie używać bibliotek opartych na tym modelu działania
- podczas kompilacji - generuje dodatkowe klasy do łączenia dependencji

Rekomendowaną biblioteką do wstrzykiwania zależności jest Hilt, która korzysta z drugiego podejścia.

---
https://developer.android.com/training/dependency-injection