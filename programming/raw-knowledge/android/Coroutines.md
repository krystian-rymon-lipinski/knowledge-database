Struktury umożliwiające odciążenie głównego wątku z czasochłonnych operacji, mogących powodować [[Android Performance|zacinanie się aplikacji]].
Podobne w swojej funkcji do wątków, są jednak znacznie "lżejsze". Każdy wątek może zawierać wiele korutyn.

```kotlin
implementation 'org.jetbrains.kotlinx:kotlinx-coroutines-android:1.3.9'
```

###### Scopes
**Każda korutyna musi zostać wywołana na zasięgu. Wówczas w momencie zniknięcia pewnego komponentu aplikacji, również korutyna zostaje zakończona.**
Pod spodem każdy `Scope` zawiera obiekt typu `CoroutineContext`.

```kotlin
viewModelScope.launch { } /* W momencie wyczyszczenia ViewModelu, korutyna również jest kończona. */
lifecycleScope.launch { } /* Fragment/Aktywność etc. W momencie ich zniszczenia, korutyna jest kończona. */
GlobalScope.launch { } /* Dopiero wyjście z aplikacji spowoduje jej zakończenie (a i to nie jest pewne, bo proces aplikacji nie musi zostać ubity! */
CoroutinesScope(chosen_dispatcher).launch { } /* Scope dziedziczący swój kontekst */
```


###### Builders
- **launch** - Dispatcher jest opcjonalny; zwraca obiekt typu **Job**, przez który można taką korutynę kontrolować (np. anulować)
- **async** - zwraca "jakikolwiek wynik"; musi zostać wywołane *await()* na obiekcie, żeby zacząć wykonywać kod w korutynie


- **withContext** - **chyba dopiero ta metoda daje gwarację na suspendowanie kodu i nie siedzenie na głównym wątku**

###### Dispatchers
Decydują, na którym wątku zostanie wykonana operacja w korutynie. Android API definiuje 3:
- Dispatchers.Default - przydatny przy złożonych obliczeniach wykorzystujących CPU
- Dispatchers.Main - przydatny przy operacjach na UI, takich jak ustawianie tekstu, ustawianie wartości LiveData, **podobno można nawet przeliczanie RecyclerView zrzucić na korutynę!**
- Dispatchers.IO - przydatny przy operacjach sieciowych oraz związanych z bazą danych


**Metoda wywoływana wewnątrz scope'u korutyny musi zostać oznaczona jako `suspend`!**
```kotlin

someScope.launch {
	someWork()
}

suspend fun someWork() {
/* tu praca */
}
```
**Blokowanie głównego wątku powoduje zamrożenie UI. Suspendowanie korutyny utworzonej na głównym wątku - nie!**




---

Każda taka **współrutyna** musi mieć swój Scope. Można go dostać poprzez ScopeBuilder.
- runBlocking - lambda zdefiniowana w bibliotece - **blokuje wątek, na którym zostaje odpalona korutyna**; czyli jeśli będzie tam jakiś delay, wątek będzie na nią czekał
- coroutineScope - nie blokuje wątku, ale trzeba oznaczyć to jako **suspend**

```kotlin
fun main() = runBlocking { /* Korutyna blokująca */
    doWorld()
}

suspend fun doWorld() = coroutineScope { /* Korutyna nieblokująca */
    launch {
        delay(1000L)
        println("World!")
    }
    println("Hello")
}
```

**launch** odpala korutynę!




https://developer.android.com/kotlin/coroutines
https://stackoverflow.com/questions/65008486/globalscope-vs-coroutinescope-vs-lifecyclescope
https://medium.com/@androidx/a-to-z-complete-tutorial-on-kotlin-coroutines-coroutine-the-black-magic-of-kotlin-e384bb4cbb4c

#status/in-progress 