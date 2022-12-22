### Biała lista
**Tablica [[0062 Adres BLE|adresów]] urządzeń BLE** zapisana w Kontrolerze, pozwalająca Hostowi filtrować urządzenia podczas rozgłaszania, skanowania, czy nawiązywania połączenia.
Filtrowanie po takiej liście można włączyć lub wyłączyć, korzystając z ustawienia *filter policy*.

Dla urządzenia rozgłaszającego będzie ona oznaczać adresy urządzeń, których zaproszenie do połączenia będzie ono akceptować.
Dla urządzenia skanującego będzie ona oznaczać adresy urządzeń, których danymi rozgłoszeniowymi jest ono zainteresowane - zarówno w kontekście nawiązywania połączenie jak i tylko obserwacji.


Filtrowanie urządzeń skanujących/rozgłaszających po adresach ma sens tylko w przypadku używania przez te urządzenia adresów niezmiennych. Używanie adresów typu *private random resolvable/non-resolvable* uniemożliwia stosowanie takiej listy - po zmianie adresu urządzenie przestanie spełniać kryteria filtra.

Urządzenia z adresem typu *private random resolvable* można zapisać w pamięci urządzenia po uprzednim nawiązaniu z nim połączenia - służy do tego [[Procedury bezpieczeństwa BLE|procedura wiązania]]. 

---
#tech-area/bluetooth-low-energy 