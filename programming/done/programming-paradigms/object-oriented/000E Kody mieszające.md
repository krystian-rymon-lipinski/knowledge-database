### Kody mieszające 
Wartości typu _Int_ klasyfikujące obiekty. Zwracane po wywołaniu metody _hashCode()_.

Wywołanie go dla tego samego obiektu powinno za każdym razem zwracać tę samą wartość. Domyślna implementacja kryje się w [natywnej implementacji JVM](https://stackoverflow.com/questions/49172698/default-hashcode-implementation-for-java-objects). [Jak?](https://srvaroa.github.io/jvm/java/openjdk/biased-locking/2017/01/30/hashCode.html)

**Jeżeli dwa obiekty mają ten sam kod mieszający, to NIE MUSZĄ BYĆ [[0005 Równość obiektów|RÓWNE]]. 
Jeżeli dwa obiekty mają być równe, to MUSZĄ MIEĆ TEN SAM KOD MIESZAJĄCY.**

Jeżeli przesłaniamy _equals()_, to trzeba też przesłonić _hashCode()_. W przeciwnym razie "\==" będzie porównywać poprawnie, ale klasa [[000C Zbiór|Set]] (korzystająca z hashCode'ów) nie będzie poprawnie wykrywać duplikatów. Najczęściej osiąga się to przez branie pod uwagę tych samych składowych klasy w obu tych metodach.

---
#tech-area/theory/programming-paradigms/object-oriented 





