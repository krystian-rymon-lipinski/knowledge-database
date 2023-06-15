up: [[013.5 Espresso MOC]]
#status/2-backlog
#tech-area/espresso

**Punkt wejścia dla _frameworku_. Zawiera metody, dzięki którym można znaleźć obiektu do testów.**

- `onView()` - przyjmuje [[ViewMatcher]] jako parametr, zwraca obiekt typu `ViewInteraction`, na którym można wywołać [[ViewAction]]; **można wywoływać na obiektach, które są w hierarchii**
- `onData()` - przyjmuje ObjectMatcher (?) jako parametr, zwraca obiekt typu `DataInteraction`; można dzięki tej metodzie załadować dane z AdapterView (np. z jakiejś listy, Spinnera lub RecyclerView), a potem ściągnąć `ViewInteraction` poprzez `atPosition()`


Istnieją też metody do pracy z Intentami: `intended()` i `intending()`.