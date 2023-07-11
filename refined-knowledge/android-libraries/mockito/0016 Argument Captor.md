up: [[001E Weryfikacja]]

**Wykorzystywany przy [[001E Weryfikacja|weryfikacji]] interakcji z Mockiem w przypadku gdy argument metody ma swoje składowe.** Służy do łapania tegoż argumentu, by później odwołać się do jego składowych (np. w celu porównania ich wartości).

**W Kotlinie inaczej łapie się Captor niż w Javie! Trzeba wykorzystać metodę `capture(captor: ArgumentCaptor<T>)` z `mockito-kotlin`!**

```kotlin
@Captor lateinit var aCaptor ArgumentCaptor<Ball> /* Deklaracja przez annotację. */
val aCaptor = ArgumentCaptor.forClass(Ball::class.java); /* A tu przez metodę. */
/* Tak zdefiniowany Captor służy do łapania obiektu typu Ball. */
```

```kotlin
class Ball {
	val radius: Int,
	val pressure: Double pressure
}
..
@Mock lateinit var game: Game
@Captor lateinit var ball: ArgumentCaptor<Ball>

verify(game).startGame(capture(ball)) /* "Złapanie" argumentu. */
val radius = ball.getValue().getRadius() /* Wyciągnięcie wartości jego składowej. */
assertEquals(20, radius)
```

Aby móc korzystać z wartości Captora, trzeba najpierw wywołać na nim _capture()_.


