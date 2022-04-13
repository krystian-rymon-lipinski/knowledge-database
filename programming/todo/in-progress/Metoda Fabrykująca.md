### Metoda Fabrykująca
**Wzorzec kreujący.**

**Metoda abstrakcyjna zawarta w klasie bazowej fabryki.** Zdefiniowanie jej implementacji spoczywa na klasach rozszerzających bazową abstrakcyjną fabrykę. Wówczas **każda taka klasa może tworzyć inne produkty.**

Tak jak w przypadku [[0055 Prosta Fabryka (-)|prostej fabryki]] - kod kliencki opiera się na **abstrakcyjnym supertypie** produktów fabryki, który muszą one implementować/rozszerzać, zamiast na pojedynczych implementacjach.

Wzorzec ten daje największe korzyści, gdy **wszystkie produkty fabryki/fabryk mają podobne zachowania**, które można związać interfejsem. Aczkolwiek utworzenie go dla tylko jednej fabryki i jego typu produktu zapewnia przynajmniej odwoływanie się do abstrakcji zamiast implementacji na poziomie klienta.

```kotlin
abstract class BallFactory {
	abstract fun createBall(type: String) : Ball 
	/* Metoda fabrykująca, zwracająca supertyp wspólny dla wszystkich produktów. */
}
class VolleyballFactory : BallFactory { 
/* Jedna z podklas definiująca implementację metody fabrykującej. */
	override fun createBall(type: String) : Ball {
		return 
			if (type == "molten") MoltenVolleyBall()
			else if (type == "mikasa") MikasaVolleyball()
			else OtherVolleyball()
	}
}
class FootballFactory : BallFactory {
/* Inna z podklas definiująca implementację metody fabrykującej. */
	override fun createBall(type: String) /* Tutaj różne typy obiektów - piłek nożnych. */
}
interface Ball {
/* Interfejs opisujący wspólne zachowania dla różnych produktów różnych fabryk. Implementuje go zarówno klasa MoltenVolleyball jak i JabulaniFootball. */
}









```

---
#tech-area/design-patterns 