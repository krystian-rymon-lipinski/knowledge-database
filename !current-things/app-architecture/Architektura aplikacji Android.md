up: [[010 Android MOC]]
#status/1-in-progress
#tech-area/android
#android/app-architecture

**Na kształt architektury wpływa fakt, że system operacyjny może w każdej chwili uwolnić część lub wszystkie zasoby, z których korzysta aplikacja. Jej dane i stan należy zatem trzymać w miejscach niezwiązanych z komponentami cyklu życia aplikacji ([[Activities|aktywnościami]], [[Fragments|fragmentami]]).**

Cele architektury:
- rozdzielenie zadań (klasy komponentów cyklu życia nie powinny zawierać całego kodu aplikacji)
- prezentowanie danych w UI na podstawie _modeli danych_ (View Models)
- pojedyncze źródło prawdy _(ang. Single Source of Truth (SSoT)_ dla danych - tylko to miejsce w kodzie może te dane zmieniać, inne miejsca w aplikacji mogą tylko wywołać metody z SSoT operujące na danych zamiast zmieniać je same
- jednostronny przepływ danych; _zdarzenia_ (np. klik w przycisk) idą w jedną stronę, aż do dojścia do SSOT, wówczas następuje uaktualnienie danych i ich przepływ w stronę UI

Warstwy aplikacji:
- [[Warstwa UI|warstwa UI]]
- [[Warstwa danych|warstwa danych]]
- [[Warstwa biznesowa|warstwa biznesowa]] (opcjonalna)

**Ponieważ poszczególne warstwy (a zatem ich klasy) zależą od siebie, należy wykorzystywać [[Wstrzykiwanie zależności|wstrzykiwanie zależności]].** Graf zależności najczęściej wygląda następująco:

```
komponent cyklu życia -> ViewModel -> (use case ->) repozytorium -> źródło danych -> serwisy/interfejsy do ściągnięcia danych
```

Dobrze jest też wykorzystać zasadę _[[SOLID|odwrócenia zależności]] (ang. dependency inversion)_ i wstrzykiwać typy abstrakcyjne, które są rozszerzane przez ich implementacje. Aczkolwiek powoduje to zwiększenie złożoności kodu, więc dla małych projektów może nie być potrzebne.














---
https://developer.android.com/topic/architecture