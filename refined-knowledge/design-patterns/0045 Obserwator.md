up: [[050 Design Patterns MOC]]
#status/revision-needed 

**Wzorzec zachowania. Pozwala powiadamiać obiekty o zdarzeniach.** Obiekt obserwowany posiada jakiś stan, którego zmianą mogą być zainteresowane inne obiekty. Ci interesanci mogą poprosić o dodanie na listę subskrybentów obiektu obserwowanego (lub usunięcie z niej). 

W momencie dokonania się jakiegoś istotnego (z punktu widzenia obiektu obserwowanego) wydarzenia, **powiadamia on obiekty go obserwujące.** Nie interesuje go ani trochę, co to za obiekty ani co zamierzają zrobić z tą informacją. 

Jedyne wymaganie jest takie, by obiekty obserwujące implementowały wspólny interfejs. Obiekt obserwowany wywoła jego metodę podczas powiadamiania poprzez **delegację** - korzystając z tego, że jest to [[0026 Metoda wirtualna|metoda wirtualna]].

Odebranie nowego stanu może dokonać się dwojako - obiekt obserwowany może wysyłać informacje w parametrach metody tak samo dla wszystkich obserwatorów lub udostępnić swoje składowe, by obserwatorzy mogli na swoich warunkach je pobierać. W pierwszym przypadku obiekt obserwowany wysyła w metodzie powiadamiającej dane, w drugim podaje w niej referencję do siebie, by można było na niej wywołać gettery. 

```kotlin
class Observable {
	val observers = arrayListOf<Observer>()

	fun registerObserver() { /* Rejestracja subskrybenta/obserwatora. */ }
	fun unregisterObserver() { /* Wyrejestrowanie go. */ }
	fun notifyObservers() { /* Powiadomienie obserwatorów. */
		observers.forEach { it.update() } /* Tak naprawdę jest to delegacja. */
	}
}

interface Observer { /* Klasy implementujące ten interfejs są obserwatorami. */
	fun update()
}
```

Dobrze jest utworzyć *Observable* jako interfejs. W przeciwnym razie będzie można skorzystać ze wzorca Obserwator tylko poprzez dziedziczenie - co będzie niemożliwe dla klas, **które już po jakiejś dziedziczą**. Wymusi to ponowne pisanie w nich kodu Obserwatora.

W przypadku interfejsu trzeba będzie zapewnić swoją implementację metod operujących na obserwatorach i powiadamiających ich. Ale przynajmniej będzie można zaimplementować go w **każdej klasie** i nie jest się skazanym na jedyną słuszną implementację klasy bazowej. Ma to również większy sens semantyczny - "oto obiekt, który robi swoje, a ponadto spełnia również rolę obiektu obserwującego i robi to w sposób, który opisują implementacje metod interfejsu Observable".

Nieco podobną strukturą do Obserwatora jest [[Callback (-)|callback]].

---
https://refactoring.guru/design-patterns/observer