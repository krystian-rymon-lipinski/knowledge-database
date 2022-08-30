### Link Layer
**Warstwa bezpośrednio powiązana z warstwą fizyczną. Jest implementowana jako mieszanka hardware'u i software'u.** Dokumentacja nakłada na nią ograniczenia czasowe, więc najczęściej jest ona izolowana od pozostałych warstw stosu protokołów interfejsem (Kontroler-Host Interfejs).

###### Hardware
Implementuje operacje wymagające obliczeniowo i łatwo automatyzowalne, takie jak:
- generacja [[0037 Pakiet BLE|podstawowych elementów pakietu BLE]] - preamble, access adress i CRC (to ostatnie jest ponadto również weryfikowane) 
- [[air protocol framing]] (?)
- [[data whitening]] (?)
- generowanie liczb losowych
- [[szyfrowanie AES]] (?)

###### Software
Definiuje [[0033 Role urządzeń BLE|rolę]] urządzenia BLE oraz stan połączenia. Każde z urządzeń może być połączone z wieloma innymi, zarówno jako Master, jak i Slave. Może również spełniać różne role jednocześnie w relacji do różnych urządzeń.

**Definiuje również [[0062 Adres BLE|adres urządzenia BLE]]**.

---
#tech-area/bluetooth-low-energy 

