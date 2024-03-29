up: [[031 Programowanie obiektowe]]

**Do obiektu można się odwoływać przez różne typy referencji.**

**Typ obiektu** pozostanie **zawsze ten sam**, ustalany w momencie jego tworzenia. 
**Typ referencji**, wskazującej na obiekt, **może się zmieniać** poprzez [[Konwersja i rzutowanie|rzutowanie]].

Typ obiektu definiuje, **co zostanie wywołane na obiekcie** - wartości i implementacje przesłanianych właściwości i metod.
Typ referencji definiuje, **co może zostać wywołane na obiekcie** - właściwości i metody, które udostępnia.



Obiekt może być polimorficzny, jeśli jego klasa [[0015 Dziedziczenie|dziedziczy]] po innej lub implementuje [[0025 Interfejs|interfejs]].
```java
class B extends A implements I {
	B obj1 = new B(); /* Obiekt typu B traktowany jako typ B. */
	A obj2 = new B(); /* Obiekt typu B traktowany jako typ A. */
	I obj3 = new B(); /* Obiekt typu B traktowany jako typ I. */
}
```
Na referencji _obj1_ można wywołać metody i składowe klasy _A_ i _B_ oraz metody interfejsu _I_.
Na referencji _obj2_ można wywołać **tylko** metody i składowe klasy _A_.
Na referencji _obj3_ można wywołać **tylko** metody interfejsu _I_.

Jeżeli na referencji _obj2_ (typ _A_) zostanie wywołana metoda klasy _A_ przesłonięta w klasie _B_, to o wybraniu konkretnej implementacji (z klasy _A_ lub _B_) decyduje fakt, czy jest to [[0026 Metoda wirtualna|metoda wirtualna]].
Jeżeli na referencji _obj3_ (typ _I_) zostanie wywołana metoda interfejsu _I_ zaimplementowana w klasie _B_, wywołana zostanie implementacja z klasy _B_, ponieważ metody interfejsu są abstrakcyjne, a więc z definicji wirtualne.

