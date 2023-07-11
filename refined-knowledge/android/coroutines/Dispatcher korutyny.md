up: [[Korutyna]]

**Decyduje, na której puli wątków zostanie wykonany kod korutyny.** Kotlin definiuje następujące _Dispatchery_:

- `Dispatchers.Main` - wykorzystywany przy operacjach na UI, ponieważ jest związany z wątkiem głównym; najczęściej tworzy się korutynę na tym właśnie _Dispatcherze_, by potem dla konkretnego bloku kodu przejść na inny poprzez `withContext()`, a po jego zakończeniu wrócić na `Main` i uaktualnić UI nowymi danymi
- `Dispatchers.IO` - wykorzystywany przy wszelakich operacjach związanych z pobieraniem danych - z sieci, bazy danych lub pliku
- `Dispatchers.Default` - wykorzystywany przy złożonych obliczeniach wykorzystujących CPU (np. parsowanie lub sortowanie)
- `StandardTestDispatcher()` - wykorzystywany do testów, by kontrolować w nich wywoływanie korutyn; wówczas nie zostają one odpalone od razu, ale po przejściu całego kodu testu; można to zmienić poprzez odpowiednią metodę w kodzie, np. `advanceUntilIdle()`
- `UnconfinedTestDispatcher()` - wykorzystywany do testów; odpala korutyny od razu po ich utworzeniu w testach

**Mimo iż `Dispatchers.Main` tworzy korutynę głównym wątku, jej blokowanie (np. poprzez `delay()` nie powoduje zamrożenia UI.**

Na potrzeby testowania dobrze jest wstrzykiwać _Dispatchery_ do konstruktora klas, które z nich korzystają - wówczas można je łatwo zamienić na testowe, które odpalają test na pojedynczym wątku, co czyni go bardziej deterministycznym. Wszystkie _TestDispatchers_ powinny być odpalone na tym samym _TestSchedulerze_.
