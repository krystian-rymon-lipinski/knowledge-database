up: [[050 Design Patterns MOC]]
#status/0-revision-needed 

**(-) Nie jest to do końca wzorzec projektowy (gdyby był, byłby kreującym). Opiera się na wydelegowaniu tworzenia różnego rodzaju obiektów (produktów fabryki) do osobnej klasy. Każdy produkt fabryki implementuje/rozszerza abstrakcyjny supertyp.** 

Dzięki temu kod kliencki nie jest uzależniony od poszczególnych implementacji. Poza tym daje to kolejną korzyść w przypadku gdy różne fragmenty kodu chcą tworzyć implementacje tychże obiektów - wówczas hermetyzacja ich kreacji do osobnej klasy (nawet jeżeli utworzonej tylko i wyłącznie po to) pozwala ograniczyć liczbę zmian w kodzie w przypadku zmiany rodzaju otrzymywanych produktów.

Zdarza się, że metoda tworząca jest zdefiniowana jako statyczna, dzięki czemu nie trzeba nawet tworzyć instancji fabryki w kodzie klienckim.

```kotlin
val ball: Ball = BallSimpleFactory.createBall("volley") 
/* Żadnych konkretnych implementacji, tylko abstrakcyjny supertyp. */

class BallSimpleFactory {
	companion object {
		fun createBall(type: String) : Ball? {
			/* Hermetyzacja zmieniających się części kodu. */
			if (type == "volley") return Volleyball()
			else null
		}
	}
}

class Volleyball : Ball {
	/* Rzeczywisty produkt fabryki implementujący supertyp. */
}
```