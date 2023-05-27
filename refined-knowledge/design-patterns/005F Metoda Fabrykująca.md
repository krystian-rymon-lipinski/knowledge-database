up: [[050 Design Patterns MOC]]
#status/0-revision-needed 

**Wzorzec kreujący.**
**Składają się na niego klasy będące fabrykami oraz klasy będące produktami fabryk.**

**Metoda abstrakcyjna zawarta w klasie bazowej.** Zdefiniowanie jej implementacji spoczywa na klasach pochodnych - wówczas mogą być one uznawane za fabryki rzeczywiste i **każda z nich może tworzyć inne produkty.**

Tak jak w przypadku [[0055 Prosta Fabryka (-)|prostej fabryki]] - produkt fabryki implementuje/rozszerza **abstrakcyjny supertyp**.
Tutaj jednakże dodatkowo każda fabryka zapewnia implementację **metody fabrykującej**.

Wzorzec ten daje największe korzyści, gdy **wszystkie produkty fabryki/fabryk mają podobne zachowania**, które można związać interfejsem. Aczkolwiek utworzenie go dla tylko jednej fabryki i jednego typu produktu zapewnia przynajmniej odwoływanie się do abstrakcji zamiast implementacji na poziomie klienta.

```kotlin
abstract class BallFactory {
	abstract fun createBall(type: String) : Ball 
	/* Metoda fabrykująca, zwracająca supertyp wspólny dla wszystkich produktów. */
}
class VolleyballFactory : BallFactory { 
/* Jedna z podklas definiująca implementację metody fabrykującej. */
	override fun createBall(type: String) : Ball {
		return 
			if (type == "molten") MoltenVolleyball()
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