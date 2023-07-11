up: [[010 Android MOC]]
#android/app-architecture
#status/0-revision-needed

**Wzorzec architektoniczny.** Następca wzorca Model-View-Presenter, ale nie wymaga interfejsu wysyłającego wiadomości Presentera do Widoku. W to miejsce Widok jest [[0045 Obserwator|Obserwatorem]] pól zdefiniowanych we ViewModelu i na każdorazową zmianę któregokolwiek jest w stanie zareagować - najczęściej po to, by zmienić wartości widoków interfejsu użytkownika.

**Widok reaguje na akcje podjęte przez użytkownika i system oraz [[0060 Kontrolowanie elementów UI|kontroluje elementy UI]] układów.**
Widokiem jest zatem Aktywność i Fragment (i być może inne klasy kontrolujące własny layout, np. Dialogi).

Dodatkowa obsługa aktualnego stanu i danych może powodować zbytnie puchnięcie klasy Widoku - dlatego właśnie dobrze jest delegować to zadanie do osobnej klasy.

---

Aby spełnić zasadę inwersji dependencji (z SOLID-a), należy zdefiniować kontrakty (interfejsy) między każdą warstwą. I tak:
- View powinien mieć dependencję do interfejsu ViewModelu (z metodami), a nie do samego ViewModelu
- ViewModel oczywiście zwraca informację do View poprzez LiveData
- ViewModel powinien mieć dependencję do interfejsu Modelu (z metodami), a nie do samego Modelu
- Powinny istnieć Modele (class xModel) dla wszystkich typów obiektów, które będą ściągane; realizuje to zasady SOLID-a: Single Responsibility oraz Interface Segregation
- Model powinien mieć dependencję do interfejsu źródła danych, a nie do samego źródła danych (np. bazy danych lub REST API)


---


**Klasy implementujące wzorzec:** 
- [[0076 ViewModel|ViewModel]]
- [[0058 LiveData|LiveData]]
- [[StateFlow]]
