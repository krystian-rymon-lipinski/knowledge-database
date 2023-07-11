up: [[Korutyna]]

**Metoda tworząca korutynę.** Domyślnie korutyna zostaje odpalona od razu i poprzez _Dispatcher_ z kontekstu dla danego zasięgu (najczęściej `Dispatchers.Main`). Android definiuje następujące _buildery_:

- `launch` - tworzy korutynę nieblokującą; zwraca obiekt typu `Job`, przez który można taką korutynę kontrolować (np. anulować poprzez `cancel()` albo poczekać na jej wykonanie poprzez `join()`); wykorzystywana dla zadań typu _fire-and-forget_, można ją tworzyć wewnątrz zwykłych funkcji
- `async` - tworzy korutynę nieblokującą; zwraca obiekt typu `Deferred<T>`, z którego można wyciągnąć dowolny typ obiektu (np. wynik obliczeń lub dane z bazy); wywołanie `await()` na typie `Deferred<T>` (lub `awaitAll()` dla listy takich obiektów) spowoduje wstrzymanie kodu, który utworzył tę korutynę, do momentu zakończenia jej pracy (i zwrócenia wartości) 
- `runTest` - używana w testach jednostkowych, aby możliwe było testowanie metod wstrzymujących (które trzeba zawołać z wewnątrz korutyny); operuje na zasięgu `TestScope` - jest to implementacja `coroutineScope`, która używa `TestDispatcher`
- `runBlocking` - tworzy korutynę blokującą; nie trzeba jej wołać na zasięgu, ale blokuje wątek, na którym została wywołana

**Wywołanie nieblokującej korutyny spowoduje współbieżne działanie kodu.**

```kotlin
lifecycleScope.launch {
	doSomething() /* Tu się coś dzieje */
}
/* A tu dzieje się coś współbieżnie */
...
suspend fun doSomething() = coroutineScope {
	val someJob = async { fetchSomeData() }
	val someData = someJob.await()
	/* Kod po await() będzie czekał na zakończenie bloku `async`*/
}
...
@Test
fun testSomething() = runTest {
	/* Umożliwia wchodzenie przez kod testu do funkcji wstrzymujących */
}
```