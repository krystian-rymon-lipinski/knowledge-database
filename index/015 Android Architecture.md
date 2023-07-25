up: [[000 HOME]]
#android/app-architecture

**Głównymi wyznacznikami dobrego kodu aplikacji jest jego skalowalność, testowalność oraz odporność na zmiany.** Nie można tego dokonać pisząc go w całości w klasach komponentów cyklu życia aplikacji (aktywności, fragmentów) - tym bardziej, że system zarządza zasobami w sposób nie do przewidzenia i może w każdym momencie ubić proces obsługujący aplikację, co spowodowałoby utratę dokonanych przez użytkownika zmian.

Z tego powodu kod jest podzielony **warstwy**:
- [[Warstwa UI|warstwa UI]]
- [[Warstwa domeny|warstwa domeny]] (opcjonalna)
- [[Warstwa danych|warstwa danych]]

Warstwy te definiują **architekturę aplikacji**, która ma za zadanie:
- rozdzielenie zadań (klasy komponentów cyklu życia nie powinny zawierać całego kodu aplikacji)
- prezentowanie danych w UI na podstawie stanu zdefiniowanego w _modelach danych_
- pojedyncze źródło prawdy _(ang. Single Source of Truth (SSoT)_ - dane aplikacji mogą być zmieniane tylko w jednym miejscu kodu
- jednostronny przepływ danych; _zdarzenia_ (np. klik w przycisk) delegują zadania do dolnych warstw aż do dojścia do SSOT; wówczas następuje uaktualnienie danych i powiadomienie o tym fakcie górnych warstw aż do zaprezentowania tych zmian w UI

Pożądana architektura najczęściej jest realizowana przy pomocy wzorców [[0056 Model-View-ViewModel|MVVM]] lub [[Model-View-Intent|MVI]].


**Ponieważ poszczególne warstwy (a zatem ich klasy) zależą od siebie, należy wykorzystywać [[Wstrzykiwanie zależności|wstrzykiwanie zależności]].** Graf zależności najczęściej wygląda następująco:

```
komponent cyklu życia -> ViewModel -> (use case ->) repozytorium -> źródło danych -> serwisy/interfejsy do ściągnięcia danych
```

Dobrze jest też wykorzystać zasadę _[[SOLID|odwrócenia zależności]] (ang. dependency inversion)_ i wstrzykiwać typy abstrakcyjne, które są rozszerzane przez ich implementacje. Aczkolwiek powoduje to zwiększenie złożoności kodu, więc dla małych projektów może nie być potrzebne.

---
https://developer.android.com/topic/architecture
https://developer.android.com/topic/architecture/recommendations