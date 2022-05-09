### Argument Captor
**Wykorzystywany przy [[001E Weryfikacja|weryfikacji]] interakcji z Mockiem w przypadku gdy argument metody ma swoje składowe.** Służy do łapania tegoż argumentu, by później odwołać się do jego składowych (np. w celu porównania ich wartości).
```java
@Captor ArgumentCaptor<Ball> aCaptor; /* Deklaracja przez annotację. */
ArgumentCaptor aCaptor = ArgumentCaptor.forClass(Ball.class); /* A tu przez metodę. */
/* Tak zdefiniowany Captor służy do łapania obiektu typu Ball. */
```

###### Przykład
```java
class Ball {
	int radius;
	double pressure;
}
..
@Mock Game game;
@Captor Ball ball;

verify(game).startGame(ball.capture()); /* "Złapanie" argumentu. */
int radius = ball.getValue().getRadius(); /* Wyciągnięcie wartości jego składowej. */
assertEquals(20, radius);
```
Aby móc korzystać z wartości Captora, trzeba najpierw wywołać na nim _capture()_.

___

#tech-area/testing/unit-testing/mockito


