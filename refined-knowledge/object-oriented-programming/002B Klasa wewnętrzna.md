up: [[0029 Klasa]]

**Klasa zdefiniowana wewnątrz innej klasy.** 
Może korzystać ze składowych i metod klasy zewnętrznej - również prywatnych.

###### Niestatyczna klasa wewnętrzna
Każda instancja niestatycznej klasy wewnętrznej jest powiązana z instancją klasy wewnętrznej - należy do niej. Aby utworzyć obiekt klasy wewnętrznej należy wywołać instrukcję tworzenia obiektu na obiekcie klasy zewnętrznej.

```java
OuterClass outer = new OuterClass();
OuterClass.InnerClass = outer.new InnerClass();
```

- może korzystać ze wszystkich elementów swojej klasy zewnętrznej.
- może deklarować tylko elementy niestatyczne.

###### Statyczna klasa wewnętrzna
Ta wersja klasy wewnętrznej nie jest powiązana z żadnym obiektem klasy zewnętrznej - jej instancje można tworzyć bez żadnego istniejącego obiektu klasy zewnętrznej.

```java
OuterClass.InnerClass inner = new OuterClass.InnerClass();
```

- może korzystać ze statycznych elementów swojej klasy zewnętrznej
- może deklarować dowolne elementy

###### Lokalna klasa wewnętrzna
Klasa wewnętrzna zdefiniowana wewnątrz bloku kodu - metody, ifa, itp. 
Można tworzyć jej obiekty tylko wewnątrz tegoż bloku.

###### [[0027 Klasa anonimowa|Klasa anonimowa]]

