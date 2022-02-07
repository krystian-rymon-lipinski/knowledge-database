### Strategia
**Wzorzec zachowania.**

**Stosowany, gdy główna klasa robi jakąś rzecz na kilka różnych sposobów.** Prawdopodobnym jest, że będzie trzeba dodać kolejny/e sposób/oby robienia tej rzeczy, co spowoduje konieczność zmieniania w niej kodu i ryzyko powstania błędów.

Rozwiązaniem jest **wyłączyć każdy z tych sposobów do swojej osobnej klasy** - każdy z nich jest właśnie **Strategią** zrobienia tej rzeczy. Ponadto każda z tych klas-strategii implementuje wspólny interfejs, a klasa główna obiekt tego interfejsu **zawiera**. 

Klasy głównej nie obchodzi, co poszczególne klasy-strategie implementują. Ona tylko **deleguje** to zadanie do nich. Dzięki temu można manipulować sposobami zrobienia rzeczy i dodawać nowe bez zmieniania kodu klasy głównej. 

Pozwala to również dynamicznie zmieniać strategie, wystarczy podmienić typ obiektu, do któego odnosi się referencja *strategy* w klasie głównej.

```kotlin
interface Strategy { 
	fun jump() /* Można skakać jak siatkarz, a można jak bramkarz. */
	/* Sposoby skakania będą implementowane przez klasy-strategie. */
}

class MainClass {
	val strategy: Strategy

	fun delegateJumping() {
		strategy.jump() /* Istotny jest typ obiektu, do którego odnosi się referencja 'strategy'. Od niego zależy, która implementacja zostanie wywołana. */
	}
}
```

Delegowanie opiera się fakcie, że metoda *jump()* jest [[0026 Metoda wirtualna|metodą wirtualną]].

---
https://refactoring.guru/design-patterns/strategy
#tech-area/design-patterns