up: [[Architektura aplikacji Android]]
#status/1-in-progress
#tech-area/android


**Warstwa danych _(ang. data layer)_ - warstwa trzymająca informacje w repozytoriach, które posiadają swoje źródła danych. Każdy typ danych powinien mieć swoje repozytorium.**

- klasy repozytoriów, które są zależne od klas źródeł danych
- klasy źródeł danych - każda z nich powinna pracować tylko z jednym źródłem danych (plikiem, lokalizacją na serwerze lub bazą danych)