up: [[050 Design Patterns MOC]]
#status/revision-needed 

**Wzorzec zachowania. Stosowany, gdy główna klasa robi jakąś rzecz na kilka różnych sposobów.** Prawdopodobnym jest, że będzie trzeba dodać kolejny/e sposób/oby robienia tej rzeczy, co spowoduje konieczność zmieniania w niej kodu i ryzyko powstania błędów.

Rozwiązaniem jest **wyłączyć każdy z tych sposobów do swojej osobnej klasy** - każdy z nich jest właśnie **Strategią** zrobienia tej rzeczy. Ponadto każda z tych klas-strategii implementuje wspólny interfejs, a klasa główna **zawiera** obiekt tego interfejsu (a dokładniej obiekt [[0027 Klasa anonimowa|klasy anonimowej]]).
Klasa główna może [[Kompozycja|komponować]] obiekty z różnym zachowaniem poprzez zawieranie większej ilości składowych tego typu.

Klasy głównej nie obchodzi, co poszczególne klasy-strategie implementują. Ona tylko **deleguje** to zadanie do nich. Delegowanie opiera się fakcie, że metoda *jump()* jest [[0026 Metoda wirtualna|metodą wirtualną]].

Dzięki temu można manipulować sposobami zrobienia rzeczy i dodawać nowe bez zmieniania kodu klasy głównej. Pozwala to również dynamicznie zmieniać strategie, wystarczy podmienić typ obiektu, do któego odnosi się referencja *strategy* w klasie głównej.

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

Pole *strategy* mogłoby równie dobrze być klasą abstrakcyjną - chodzi tylko o to, by każda konkretna strategia miała **wspólny supertyp na potrzeby delegacji**.

Zastosowanie tego wzorca ma sens wówczas, gdy **strategie są wykorzystywane przez różne typy obiektów** (np. przez podklasy klasy głównej) lub gdy **strategie te mogą się zmieniać dla konkretnego typu obiektu**. W przeciwnym razie należy się zastanowić, czy dziedziczenie nie jest wystarczające.

---
https://refactoring.guru/design-patterns/strategy