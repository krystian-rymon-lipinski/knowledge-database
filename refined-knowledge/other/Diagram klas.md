up: [[110 UML]]

**Opisuje szczegółową implementację pojedynczego komponentu systemu poprzez klasy, interfejsy oraz relacje między nimi.** Elementy diagramu mogą mieć swoje atrybuty - pola i metody. Mogą one być prywatne, publiczne lub chronione.

Możliwe są różne relacje między elementami diagramu, z których każda oznaczona jest inną strzałką.
- [[0015 Dziedziczenie|dziedziczenie]]
- realizacja (implementacja) - określony sposób wypełnienia przez klasę kontraktu zdefiniowanego interfejsem

- zależność - relacja jednokierunkowa: obiekt klasy A używa obiektu klasy B, np. tworząc go, wywołując jego metody lub zwracając go w swojej metodzie; zmiana kodu klasy B może oznaczać konieczność zmiany kodu w klasie A; szczególną formą zależności jest [[Wstrzykiwanie zależności|wstrzykiwanie zależności]]
- asocjacja - obiekty dwóch klas są ze sobą powiązane; najczęściej oznacza to, że obiekt klasy A trzyma obiekt klasy B jako pole; może to działać w dwie strony i w różnych ilościach
- agregacja - szczególniejsza forma asocjacji, reprezentująca relację "MA"; obiekt klasy B składa się na obiekt klasy A (jest jego częścią), ale może istnieć również w innym kontekście - zniszczenie obiektu klasy A nie powoduje zniszczenia obiektów klasy B
- kompozycja - szczególniejsza forma agregacji, gdzie obiekt klasy B nie istnieje w innym kontekście jak tylko część całości składającej się na obiekt klasy A; zniszczenie obiektu klasy A powoduje zniszczenie obiektu klasy B

![[uml_relations.png]]

Książki mogą istnieć bez regału - agregacja.
Zniszczenie regału oznacza zniszczenie również półek - kompozycja.

---
[http://www.cs.utsa.edu/~cs3443/uml/uml.html](http://www.cs.utsa.edu/~cs3443/uml/uml.html)
https://nirajrules.wordpress.com/2011/07/15/association-vs-dependency-vs-aggregation-vs-composition/