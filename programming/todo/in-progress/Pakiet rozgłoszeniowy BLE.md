### Pakiet rozgłoszeniowy BLE
**Jeden z typów pakietu BLE. Transmitowany na [[Kanały BLE|kanale]] rozgłaszania.**

**Używany do:
- [[Rozgłaszanie|rozgłaszania]]
- obsługi [[Scan Request|dodatkowego zapytania]] 
- inicjowania połączenia.

Każdy z tych scenariuszy ma taki sam format danych protokołowych pakietu.

###### Header (2 bajty)
- [[Typy pakietu rozgłaszania|typ pakietu rozgłaszania]] (4 bity)
- 2 bity puste (na kolejne typy pakietów w przyszłości)
- typ adresu urządzenia rozgłaszającego; 1 dla przypadkowego, 0 dla publicznego (1 bit)
- typ adresu urządzenia docelowego; 1 dla przypadkowego, 0 dla publicznego (1 bit)
- długość danych urządzenia (6 bitów)
- 2 bity puste (na zwiększenie długości danych urządzenia w przyszłości)

###### Dane urządzenia (6-37 bajtów)
- adres urządzenia rozgłaszającego (6 bajtów) - obecny zawsze
- [[Dane rozgłoszeniowe|dane rozgłoszeniowe]] (0-31 bajtów) - obecne w przypadku rozgłaszania

---
#tech-area/bluetooth-low-energy 