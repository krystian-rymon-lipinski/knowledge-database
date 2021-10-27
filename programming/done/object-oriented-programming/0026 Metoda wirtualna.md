### Metoda wirtualna
**Metoda, której wywołanie jest polimorficzne. Wywołuje implementację bazując na typie obiektu, a nie na typie referencji do niego.**

W założeniu taka metoda zostanie przesłonięta w różnych klasach z inną implementacją w każdej z nich. Wówczas dla każdej klasy wywoła się inna implementacja pomimo użycia dla każdej z nich referencji tego samego bazowego typu.

```java
class A {			
	void foo();			
}		
class B extends A {}
	void foo(); /* Przesłonięcie metody z klasy bazowej. */
}
A obiektBazowy = new A();
A obiektPochodny = new B(); /* Obiekt jest typu B. Referencja do niego - typu A. */

obiektBazowy.foo(); /* Wykonana zostanie metoda z klasy A. Zawsze. */
obiektPochodny.foo(); /* ? */
```
Jeżeli metoda _foo()_ jest wirtualna, _obiektPochodny.foo()_ wywoła metodę z klasy _B_, ponieważ bazuje na typie obiektu, a referencja _obiektPochodny_ wskazuje na obiekt typu B.
Jeżeli metoda _foo()_ nie jest wirtualna, _obiektPochodny.foo_ wywoła metodę z klasy _A_, ponieważ bazuje na typie referencji do obiektu, a referencja _obiektPochodny_ jest typu A.

**W Javie i jej pochodnych wszystkie metody są domyślnie wirtualne!**

---
#tech-area/theory/programming-paradigms/object-oriented 