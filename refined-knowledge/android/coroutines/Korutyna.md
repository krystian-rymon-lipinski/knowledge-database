up: [[020 Kotlin MOC]]
#android/gradle-dependency #android/multithreading

```kotlin
implementation("org.jetbrains.kotlinx:kotlinx-coroutines-android:1.3.9")
testImplementation("org.jetbrains.kotlinx:kotlinx-coroutines-test:$coroutines_version")
```

**Koncept rozszerzający metodę. Umożliwia wykonywanie czasochłonnych zadań bez blokowania głównego wątku poprzez wykorzystywanie [[Funkcja wstrzymująca|funkcji wstrzymujących]]**.

Właściwe użytkowanie korutyn poprawia [[Android Performance|osiągi]] aplikacji. Są podobne w swojej funkcji do wątków, będąc jednocześnie znacznie "lżejsze". Każdy wątek może zawierać wiele korutyn.

- [[Kontekst korutyny|kontekst korutyny]]
- [[Zasięg korutyny|zasięg korutyny]]
- [[Builder korutyny|builder korutyny]]
- [[Dispatcher korutyny|dispatcher korutyny]]

[Testowanie korutyn](https://developer.android.com/kotlin/coroutines/test) jest możliwe dzięki definiowaniu testowych zasięgów i _dispatcherów_.

---
https://kotlinlang.org/docs/coroutines-guide.html
https://developer.android.com/kotlin/coroutines