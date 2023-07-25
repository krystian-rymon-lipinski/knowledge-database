up: [[015 Android Architecture]]

**Warstwa danych _(ang. data layer)_ - warstwa pobierająca informacje do wyświetlenia w aplikacji. Składa się z klas repozytoriów i klas źródeł danych. 

Klasy repozytoriów zależą od klas źródeł danych i - jeżeli jest ich więcej - rozwiązują ewentualne konflikty powstałe przy ściągnięciu danych z różnych miejsc (dokonują synchronizacji). Następnie udostępniają owe dane wyższym warstwom aplikacji. **Każdy typ danych obecny w aplikacji powinien mieć swoje repozytorium.**

Klasy źródeł danych powinny pracować tylko z jednym źródłem danych - lokalnym (plikiem, obiektem [[SharedPreferences]] lub [[013.6 Room|bazą danych Room]]) lub zdalnym (lokalizacją na serwerze ściąganą przez [[090 REST|interfejs REST]]). Dane te powinny być udostępnianie klasom repozytoriów poprzez [[Przepływ|przepływy]].

Obiekty klas repozytoriow i źródeł danych mogą mieć różny zasięg, w zależności od tego, czy któryś z nich jest np. czasochłonny do utworzenia albo ma wewnętrzny stan, który się zmienia. Zasięg globalny powinny mieć:
- baza danych Room
- serwis Retrofit

Dane przychodzące ze źródła najczęściej zawierają więcej informacji na temat obiektu niż wymagane do wyświetlenia. Dlatego należy zdefiniować model (klasę danych) na potrzeby źródła danych oraz osobny dla wyższych warstw aplikacji. Dobrze jest to zrobić nawet jeżeli oba te obiekty składają się z tych samych elementów, pozwala to bowiem uchronić klasy wyższych warstw od zmian w kodzie, gdy zmieni się struktura danych przychodzących ze źródła.

**Rekomendowanym źródłem danych jest lokalne, np. baza danych.** W ten sposób można zapewnić źródło prawdy dla danych nawet w przypadku bycia poza siecią. Jeśli aplikacja korzysta z danych z internetu, można rozważyć ich *caching*. Jest to tzw. budowanie aplikacji _offline-first_.