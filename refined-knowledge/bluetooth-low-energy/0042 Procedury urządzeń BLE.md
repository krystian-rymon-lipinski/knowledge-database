**Akcje podejmowane przez urządzenia obserwujące, czyli pracujące w [[0033 Role urządzeń BLE|rolach]] Obserwatora i Urządzenia Centralnego, w celu odebrania danych od urządzenia nadającego i ewentualnie nawiązania z nim połączenia.**

**Observation** - obserwowanie bez chęci nawiązania połączenia; odbierane będą tylko dane rozgłoszeniowe

**Limited discovery** - obserwowanie w poszukiwaniu danych rozgłoszeniowych z [[0036 Flagi rozgłaszania|flagą]], sugerującą odpowiedni tryb (Limited Discoverable); urządzenia rozgłaszające się w ten sposób zostaną przekazane do aplikacji jako kandydaci do nawiązania połączenia

**General discovery** - obserwowanie w poszukiwaniu danych rozgłoszeniowych z [[0036 Flagi rozgłaszania|flagą]] sugerującą odpowiedni tryb (Limited Discoverable, General discoverable); urządzenia rozgłaszające się w ten sposób zostaną przekazane do aplikacji jako kandydaci do nawiązania połączenia

**Auto connection establishment** - dodanie na [[0068 Biała lista|białą listę]] adresów urządzeń peryferyjnych i połączenie się z pierwszym z nich, które zostanie wyskanowane 

**General connection establishment** - ogólne skanowanie bez filtrów; do aplikacji przekazane zostaną wszystkie wyskanowane urządzenia, by to użytkownik zadecydował, z którym z nich się połączyć; po wybraniu urządzenia wykonana zostanie procedura *direct connection establishment*

**Selective connection establishment** - procedura podobna do *General connection establishment*, z jedyną różnicą, że na skanowanie nałożony zostaje filtr adresów znajdujących się na białej liście; inne urządzenia nie zostaną przekazane do aplikacji jako wykryte

**Direct connection establishment** - próba połączenia do konkretnego urządzenia peryferyjnego (z określonym adresem) bez uprzedniego skanowania; może się nie powieść z uwagi na nieobecność urządzenia lub jego bycie w trybie non-connectable

Poszczególne procedury są powiązane z odpowiadającymi im [[0034 Tryby urządzeń BLE|trybami]].
Ponadto zdefiniowano [[0035 Procedury połączenia BLE|dodatkowe procedury]] wykorzystywane dla istniejącego już połączenia.
