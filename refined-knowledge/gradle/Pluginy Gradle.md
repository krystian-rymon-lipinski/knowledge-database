up: [[060 Gradle MOC]]

Gradle jako narzędzie samo w sobie nie daje większych możliwości automatyzacji. Do tego służą pluginy, które **definiują dodatkowe zadania, obiekty, konwencje, konfiguracje**, etc., które można później **wykorzystać w skrypcie `build.gradle`** (na poziomie projektu i w każdym z modułów).

Aby użyć pluginu, Gradle najpierw musi go najpierw znaleźć *(ang. resolve)*. Następnie ten plugin trzeba zastosować *(ang. apply)* i wówczas można korzystać z funkcjonalności jakie oferuje.

Gradle rozróżnia *core plugins* i *community plugins*. Lista tych pierwszych dostępna jest [tutaj](https://docs.gradle.org/current/userguide/plugin_reference.html) - nie trzeba ich znajdować, są one gotowe do zastosowania. Wyszukiwarka tych drugich znajduje się [tutaj](https://plugins.gradle.org/).

###### Typy pluginów
- [[Pluginy binarne Gradle|pluginy binarne Gradle]]
- [[Pluginy skryptowe Gradle|pluginy skryptowe Gradle]]

---
https://docs.gradle.org/current/userguide/plugins.html