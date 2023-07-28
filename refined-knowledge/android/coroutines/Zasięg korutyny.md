up: [[Korutyna]]

**Każda korutyna musi zostać wywołana wewnątrz obiektu zasięgu. Blok zasięgu nie zakończy się (i nie zwróci wartości), dopóki nie zakończą pracy wszystkie korutyny stworzone wewnątrz niego.** Można go anulować, co wiąże się z anulowaniem aktualnie wykonywanych korutyn oraz niemożnością utworzenia nowych.

Parametrami zasięgu są elementy [[Kontekst korutyny|kontekstu]] - każda korutyna wywołana na danym zasięgu domyślnie będzie z nich korzystać.

```kotlin
val scope = CoroutineScope(Job() + Dispatchers.Main)
scope.launch { /* Praca do wykonania w korutynie */ }
scope.cancel()
```

Biblioteki Androida definiują zasięgi powiązane z konkretnym komponentem aplikacji, które wraz z ich zniszczeniem automatycznie anulują zasięgi oraz ich ewentualne aktywne korutyny.

```kotlin
viewModelScope.launch { } 
lifecycleScope.launch { } /* Np. Aktywność lub Fragment */
backgroundScope.launch { } /* Do testowania - anulowany wraz z zakończeniem testu */
GlobalScope.launch { } /* Powiązany z komponentem Application (lub nawet jej procesem) */
```

Wewnątrz korutyny można również skorzystać z funkcji wstrzymujących definiowanych przez Androida, które dziedziczą kontekst - a zatem i zasięg - co umożliwia tworzenie kolejnych korutyn.

```kotlin
coroutineScope { launch { /* Work */} }
withContext(Dispatchers.IO) { launch { /* Work */ } }
withTimeout(1000L) { launch { } } /* Zwraca wyjątek, gdy korutyna nie zdąży w czasie */
withTimeoutOrNull(1000L) { launch { } } /* Zwraca null zamiast wyjątku */
```

---
https://developer.android.com/kotlin/coroutines/coroutines-adv#coroutinescope
