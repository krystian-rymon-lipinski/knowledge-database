up: [[Architektura aplikacji Android]]
#status/1-in-progress
#tech-area/android


**Warstwa danych _(ang. data layer)_ - warstwa trzymająca informacje w repozytoriach, które posiadają swoje źródła danych. Każdy typ danych powinien mieć swoje repozytorium.**

- klasy repozytoriów, które są zależne od klas źródeł danych
- klasy źródeł danych - każda z nich powinna pracować tylko z jednym źródłem danych (plikiem, lokalizacją na serwerze lub bazą danych)

Klasy repozytoriów zależą od klas źródeł danych i - jeżeli jest ich więcej - rozwiązują konflikty powstałe przy ściągnięciu różniących się w jakiś sposób między sobą.

Trzeba zdecydować, jaki scope powinny mieć repozytoria i/lub źródła danych podczas ich wstrzykiwania. W zależności od tego, czy któryś z tych obiektów jest np. czasochłonny do utworzenia albo ma wewnętrzny stan, który się zmienia.

Globalny scope powinny mieć:
- baza danych Room
- serwis Retrofit

Może też się zdarzyć, że dane ze źródła przyjdą w większej liczbie, niż potrzebne - na przykład z REST API z serwera przychodzi tego więcej. Wówczas w klasie repozytoriów trzeba to obciąć do tych danych, których używa aplikacja poprzez _data class_ modeli. **Modele to dane, z których korzystają repozytoria (albo klasy źródeł danych w sumie) po przerobieniu ich z miejsc, z których je dostają.**