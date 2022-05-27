### Model-View-ViewModel
**Wzorzec architektoniczny.** Następca wzorca Model-View-Presenter, ale nie wymaga interfejsu wysyłającego wiadomości Presentera do Widoku. W to miejsce Widok jest [[0045 Obserwator|Obserwatorem]] pól zdefiniowanych we ViewModelu i na każdorazową zmianę któregokolwiek jest w stanie zareagować - najczęściej po to, by zmienić wartości widoków interfejsu użytkownika.

**Widok jest kontrolerem widoków interfejsu użytkownika.**
Widokiem jest zatem Aktywność i Fragment (i być może inne klasy kontrolujące własny layout, np. Dialogi).

Głównym ich przeznaczeniem jest kontrolowanie UI oraz reagowanie na akcje podjęte przez użytkownika i system. Dodatkowa obsługa aktualnego stanu i danych może powodować zbytnie puchnięcie klasy Widoku - dlatego właśnie dobrze jest delegować to zadanie do osobnej klasy.
	
**Implementacja w Androidzie:** 
- [[0057 ViewModel|ViewModel]]
- [[0058 LiveData|LiveData]]

---
#tech-area/design/architectural-patterns
