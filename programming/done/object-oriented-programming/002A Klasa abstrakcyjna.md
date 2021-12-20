### Klasa abstrakcyjna
**Klasa, której instancji nie można utworzyć. Służy tylko i wyłącznie do tego, by ją rozszerzać i tworzyć obiekty klas pochodnych.**

W klasie abstrakcyjnej można definiować metody zwykłe jak i abstrakcyjne.
Zdefiniowanie choć jednej metody jak abstrakcyjnej zmusza do zdefiniowania całej klasy jako abstrakcyjnej.

###### Metoda abstrakcyjna
**Metoda bez implementacji. Służy tylko i wyłącznie do tego, by ją przesłonić w klasie pochodnej.**

**Wszystkie metody abstrakcyjne trzeba przesłonić w klasie pochodnej!**

W ten sposób można definiować różne zachowania dla różnych klas pochodnych, a jednocześnie mieć pewność, że każda z nich zapewni zestaw zachowań wymaganych przez klasę abstrakcyjną.
