### Model-View-ViewModel
**Wzorzec architektoniczny.** Następca wzorca Model-View-Presenter, ale nie wymaga interfejsu wysyłającego wiadomości Presentera do Widoku. W to miejsce Widok jest [[0045 Obserwator|Obserwatorem]] pól zdefiniowanych we ViewModelu i na każdorazową zmianę któregokolwiek jest w stanie zareagować - najczęściej po to, by zmienić wartości widoków interfejsu użytkownika.

**Widok reaguje na akcje podjęte przez użytkownika i system oraz [[0060 Kontrolowanie elementów UI|kontroluje elementy UI]] układów.**
Widokiem jest zatem Aktywność i Fragment (i być może inne klasy kontrolujące własny layout, np. Dialogi).

Dodatkowa obsługa aktualnego stanu i danych może powodować zbytnie puchnięcie klasy Widoku - dlatego właśnie dobrze jest delegować to zadanie do osobnej klasy.


**Implementacja w Androidzie:** 
- [[ViewModel|ViewModel]]
- [[0058 LiveData|LiveData]]

---
#tech-area/design/architectural-patterns
