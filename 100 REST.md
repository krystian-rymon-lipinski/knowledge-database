up: [[000 HOME]]

**REST _(ang. REpresentational State Transfer)_** - **wzorzec architektoniczny dla serwisów internetowych. Najczęściej korzysta z protokołu HTTP.** Możliwe jest oparcie architektury na innym, ale będzie się to wiązało z utratą kompatybilności z serwisami opartymi na HTTP oraz niemożnością skorzystania z bibliotek i narzędzi dla tego protokołu stworzonych (czyli znakomitej większości).

Jest on definiowany przez swoje ograniczenia:
- architektura klient-serwer - oddzielenie interfejsu użytkownika od danych
- bezstanowość - serwer nie przechowuje żadnego stanu, klient musi dostarczyć wszystkie wiadomości potrzebne do przetworzenia zapytania; stan sesji trzymany jest zatem po stronie klienta
- cache - odpowiedź na zapytanie przychodząca z serwera zawiera informację o tym, czy dane są możliwe do _scache'owania_; jeśli tak, można wykorzystać te dane do formowania kolejnych zapytań
- **jednolity interfejs - wszystkie zapytania i odpowiedzi muszą mieć ustandaryzowaną strukturę**; jedną z najczęstszych implementacji jest [[Interfejs REST HTTP|interfejs REST po protokole HTTP]] 
- architektura warstwowa - każda warstwa systemu widzi tylko tą, z którą się komunikuje, nie pojęcia o całym systemie
- (opcjonalne rozszerzenia - możliwość pobierania i instalowania dodatkowych skryptów przez klienta)

**Jednostką informacji w tym wzorcu jest [[Zasób REST|zasób]].**

Interfejs jest definiowany przez następujące własności:
- identyfikacja zasobów - każdy zasób biorący udział w interakcji klient-serwer musi mieć swój unikalny identyfikator
- reprezentacja zasobów - zasoby powinny mieć jednolitą reprezentację opisującą ich stan, którym klient może manipulować 
- samoopisujące wiadomości - każda reprezentacja zasobów powinna dostarczać informacje o sposobie ich procesowania oraz dodatkowych akcji, które można na niej wykonać
- klient powinien znać tylko URI aplikacji/strony; wszelkie akcje na zasobach (ściąganie/aktualizowanie stanu, etc.) powinny być dostępne poprzez linki (np. serwer w odpowiedzi na zapytanie może dostarczyć link do powiązanego zasobu)

---
https://restfulapi.net/
https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm