### Dekorator 
**Wzorzec strukturalny.**

**Pozwala rozszerzać zachowania obiektów o dodatkowe czynności.** Opiera się na **rekurencyjnej kompozycji** oraz **wspólnym typie obiektów dekorowanych i ich dekoratorów.**

Podstawą hierarchii klas dla tego wzorca jest interfejs, opisujący zachowania, które mogą być później rozszerzane. Obiekt dekorowany implementuje ten interfejs, definiując podstawowe zachowanie obiektu. Jednocześnie ten sam interfejs jest implementowany przez abstrakcyjny dekorator, który będzie klasową bazową dla konkretnych dekoratorów.

```kotlin
interface Sandwich { /* Zachowania obiektu, które mogą być rozszerzane. */
	fun eat() 
}
class BaseSandwich implements Sandwich { /* Obiekt dekorowany. */
	override fun eat { "Just bread and butter." }
}
class CheeseDecorator(val baseSandwich: BaseSandwich) extends BaseSandwichDecorator() {
	override fun eat() { baseSandwich.eat() + "With cheese." } /* Konkretny dekorator.*/ 
	/* Deleguje wykonanie metodu poziom niżej i dodaje coś od siebie. */
}
...
fun decoratorTest() {
	val baseSandwich = BaseSandwich() /* Bazowy obiekt. */
	val decoratedSandwich = CheeseDecorator(baseSandwich) 
	/* Zawinięcie bazowego obiektu dekoratorem. */
}
```

Można zastosować więcej dekoratorów naraz. Najbardziej zewnętrzny **wydeleguje** wykonanie jej do swojego obiektu-pola o tym samym typie. Jeśli ten obiekt również jest dekoratorem (ma swój obiekt-pole o tym samym typie), on również wydeleguje wykonanie tej metody poziom niżej. Będzie to postępowało rekurencyjnie, aż do momentu w którym obiekt-pole dekoratora okaże się być obiektem dekorowanym, który zamiast następnej delegacji posiada konkretną implementację metody. Wówczas to posiadając bazową implementację kod wraca przez wszystkie poziomy dekoratorów, z których każdy dodaje coś od siebie - dekoruje obiekt bazowy.

**W danej hierarchii mogą istnieć różne typy obiektów dekorowanych** - mogą różnie implementować metodę bazowego interfejsu. **Zastosowanie Dekoratora ma największy sens, gdy typ obiektu dekorowanego nie ma znaczenia** - i istotne jest tylko to, że implementuje on metody interfejsu bazowego. Jeśli któryś z typów obiektów dekorowanych definiuje jakieś specjalne zachowania (których inne typy nie mają), wtłoczenie go w ramy tego wzorca może okazać się problematyczne. 

*Dekorator* pozwala **dodawać różne zachowania**, podczas gdy *[[0044 Strategia]]* ma za zadanie **definiować różne implementacje danego zachowania**.

---
https://refactoring.guru/design-patterns/decorator
#tech-area/design-patterns 