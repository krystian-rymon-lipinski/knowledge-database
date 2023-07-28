up: [[000 HOME]]
#android/app-architecture

**Głównymi wyznacznikami dobrego kodu aplikacji jest jego skalowalność, testowalność oraz odporność na zmiany.** Nie można tego dokonać pisząc go w całości w klasach komponentów cyklu życia aplikacji (aktywności, fragmentów) - tym bardziej, że użytkownik zarządza zasobami w sposób nie do przewidzenia (system androidowy trochę też) i może w każdym momencie ubić proces obsługujący aplikację, co spowodowałoby utratę dokonanych w niej zmian.

Z tego powodu kod jest podzielony **warstwy**:
- [[Warstwa UI|warstwa UI]]
- [[Warstwa domeny|warstwa domeny]] (opcjonalna)
- [[Warstwa danych|warstwa danych]]

Warstwy te definiują **architekturę aplikacji**, która ma za zadanie:
- rozdzielenie zadań (klasy komponentów cyklu życia nie powinny zawierać całego kodu aplikacji)
- prezentowanie danych w UI na podstawie stanu zdefiniowanego w _modelach danych_
- pojedyncze źródło prawdy _(ang. Single Source of Truth (SSoT)_ - dane aplikacji mogą być zmieniane tylko w jednym miejscu kodu
- jednostronny przepływ danych; _zdarzenia_ (np. klik w przycisk) delegują zadania do dolnych warstw aż do dojścia do SSOT; wówczas następuje uaktualnienie danych i powiadomienie o tym fakcie górnych warstw aż do zaprezentowania tych zmian w UI


**Poszczególne warstwy (a raczej ich klasy) zależą od siebie, do ich łączenia należy wykorzystywać [[Wstrzykiwanie zależności|wstrzykiwanie zależności]].** Graf zależności pomiędzy nimi oraz API i/lub biblioteki, z których korzystają przedstawia [[Mapa architektury Android|mapa architektury]].

Dobrze jest też wykorzystać zasadę _[[SOLID|odwrócenia zależności]] (ang. dependency inversion)_ i wstrzykiwać typy abstrakcyjne, które są rozszerzane przez ich implementacje. Pomaga to zamieniać implementacje podczas testów, aczkolwiek powoduje również zwiększenie złożoności kodu, więc dla małych projektów może nie być potrzebne.

Pożądana architektura najczęściej jest realizowana przy pomocy wzorców [[0056 Model-View-ViewModel|MVVM]] lub [[Model-View-Intent|MVI]].

---
https://developer.android.com/topic/architecture
https://developer.android.com/topic/architecture/recommendations