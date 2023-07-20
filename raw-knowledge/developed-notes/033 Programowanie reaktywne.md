up: [[030 Paradygmaty programowania]]
#status/3-freezer
#tech-area/programming-paradigms

**Paradygmat opierający się na strumieniach, generujących dane asynchronicznie, oraz obserwatorach śledzących te strumienie.** Wykorzystuje on wzorzec projektowy [[0045 Obserwator|Obserwator]].

- producent/emiter - emituje dane, które są dodawane do strumienia
- pośrednik - może modyfikować dane emitowane do strumienia lub sam strumień
- konsument/kolektor - odbiera dane ze strumienia

Istnieją dwa typy strumieni: 
- zimne _(ang. cold streams)_ - produkuje wartości dopiero, gdy kolektor zacznie go subskrybować; emituje te same wartości (cały strumień) wszystkim subskrybentom
- gorące _(ang. hot streams_) - jego instancja istnieje niezależnie od tego, czy istnieją kolektory go subskrybujące; emituje wartości nawet jeśli nic ich nie odbiera; kolektor odbiera wartości wyprodukowane przez strumień tylko od momentu subskrybowania zamiast wszystkich od początku istnienia strumienia

_upstream_ vs. _downstream_ - czasami emitowanie nowych danych do strumienia (_upstream_) następuje szybciej niż ich przetworzenie (skonsumowanie) i wyświetlenie na ekranie (_downstream_); podobno można jakoś tym sterować (?)

[[RxJava]], RxKotlin, RxAndroid
[[Przepływ|Kotlin flows]]

---
https://gist.github.com/staltz/868e7e9bc2a7b8c1f754