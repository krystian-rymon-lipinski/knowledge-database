Takie jakby mini-wątki. Ale może być ich dużo nawet w jednym wątku.

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
