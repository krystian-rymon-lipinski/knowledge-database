up: [[0029 Klasa]]

**Służy do zdefiniowania obiektu, który ma typ [[0025 Interfejs|interfejsu]]**. Nie można jednak stworzyć instancji interfejsu, więc za kulisami utworzona zostaje klasa go implementująca.

```java
interface Example { /* Definicja interfejsu */
	void foo();
}
...
Example ci = new Example() { /* Początek klasy anonimowej */
	@Override 
	void foo() { /* Implementacja abstrakcyjnej metody */ }
}
```

Referencja _ci_ jest typu Example, więc może wykorzystać metody interfejsu. 

Teoretycznie do obiektu można się też odwołać poprzez typ klasy anonimowej, ale nie zawiera ona żadnych metod ani składowych, z których można by skorzystać. Powstała tylko po to, by implementować interfejs, dlatego jej typ nie jest istotny (jest anonimowa).

Za kulisami wygląda to tak:

```java
class ExampleImpl implements Example {
	@Override
	void foo() { /* Implementacja abstrakcyjnej metody */ }
} /* Nic poza interfejsem. */
...
Example ci = new ExampleImpl(); /* Referencja typu Example, tylko taka potrzebna. */
```