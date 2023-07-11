up: [[Korutyna]]

**Obiekt opisujący korutynę poprzez kilka elementów.**
- `Job()` - kontroluje cykl życia korutyny, można ją poprzez ten obiekt np. anulować
- `CoroutineDispatcher` - [[Dispatcher korutyny|dispatcher korutyny]]
- `CoroutineName` - nazwa korutyny; raczej potrzebna tylko do debugowania
- `CoroutineExceptionHandler` - zajmuje się niezłapanymi wyjątkami

Można zmienić kontekst aktualnie wykonywanej korutyny poprzez funkcję wstrzymującą `withContext()`. Najczęściej jest ona wykorzystywana, by przenieść korutynę na inną pulę wątków.

```kotlin
suspend fun fetchDocs() {                      // Dispatchers.Main    
	val result = get("developer.android.com")  // Dispatchers.Main    
	show(result)                               // Dispatchers.Main
}
suspend fun get(url: String) =                 // Dispatchers.Main
	withContext(Dispatchers.IO) {              // Dispatchers.IO (main-safety block)        /* Some work here */                       // Dispatchers.IO (main-safety block)   
	}                                          // Dispatchers.Main
}
```

Używanie `withContext()` jest uważane za dobrą praktykę, ponieważ czyni to funkcje [[Bezpieczeństwo wątku głównego|bezpiecznymi dla wątku głównego]]. Inne miejsca w kodzie mogą po prostu zawołać konkretną metodę z wątku głównego - metoda sama zatroszczy się o przeniesienie czasochłonnych operacji na inny.