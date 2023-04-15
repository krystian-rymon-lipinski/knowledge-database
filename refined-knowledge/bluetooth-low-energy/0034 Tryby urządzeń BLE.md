**Zachowania urządzeń nadających, czyli pracujących w [[0033 Role urządzeń BLE|rolach]] Transmitera i Urządzenia Peryferyjnego, w celu rozgłoszenia swojej obecności.**
Definiowane są poprzez [[0041 Typy rozgłaszania|typy rozgłaszania]] i [[0036 Flagi rozgłaszania|flagi]] - zawarte w danych rozgłoszeniowych.

**Broadcast** - urządzenie nadaje dane rozgłoszeniowe o typie bez możliwości utworzenia połączenia (ADV_NONCONN_IND, ADV_SCAN_IND)

**Non-discoverable** - urządzenie może nadawać dane rozgłoszeniowe, ale nie chce być znalezione przez inne urządzenia; flagi oznaczające wykrywalność urządzenia muszą być ustawione na 0, wysyłane pakiety zaś tylko tych samych typów jak dla trybu broadcast

**Limited discoverable** - urządzenie rozgłasza się przez ograniczony czas; wymaga ustawienia odpowiedniej flagi; tryb raczej już nieużywany

**General discoverable** - urządzenie rozgłasza się tak długo, jak chce - albo do momentu nawiązania połączenia; wymaga ustawienia odpowiedniej flagi

**Non-connectable** - urządzenie nie nadaje danych rozgłoszeniowych lub nadaje pakiety o typie bez możliwości utworzenia połączenia (ADV_NONCONN_IND, ADV_SCAN_IND); nie jest zainteresowane nawiązaniem połączenia

**Directed connectable** - urządzenie nadaje dane rozgłoszeniowe o typie ADV_DIRECT_IND; wysyła je z dużą częstotliwością i przez krótki czas, bez żadnych danych rozgłoszeniowych poza adresem celu; tylko urządzenie z tym adresem będzie w stanie odebrać komunikat; tryb ten wykorzystywany jest do szybkiego ponownego połączenia, np. dla przykład dla urządzeń, które często pracują razem

**Undirected connectable** - urządzenie nadaje dane rozgłoszeniowe o typie ADV_IND; główny sposób urządzeń peryferyjnych na ogłoszenie gotowości do nawiązania połączenia

Poszczególne tryby są powiązane z odpowiadającymi im [[0042 Procedury urządzeń BLE|procedurami]].