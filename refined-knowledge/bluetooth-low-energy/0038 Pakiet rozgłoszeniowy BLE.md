up: [[0037 Pakiet BLE]]

**Jeden z rodzajów pakietu BLE. Transmitowany na [[0043 Kanały BLE|kanałach rozgłaszania]].**

**Używany do:
- [[003A Rozgłaszanie|rozgłaszania]]
- obsługi [[003B Scan Request|dodatkowego zapytania]] 
- inicjowania połączenia

Każdy z tych scenariuszy ma taki sam format danych protokołowych pakietu.

###### Header (2 bajty)
- [[003C Typy pakietu rozgłoszeniowego|typ pakietu rozgłoszeniowego]] (4 bity)
- 2 bity puste (na kolejne typy pakietów w przyszłości)
- typ adresu urządzenia rozgłaszającego; 1 dla przypadkowego, 0 dla publicznego (1 bit)
- typ adresu urządzenia docelowego; 1 dla przypadkowego, 0 dla publicznego (1 bit)
- długość danych urządzenia (6 bitów)
- 2 bity puste (na zwiększenie długości danych urządzenia w przyszłości)

###### Dane (0-37 bajtów)
W zależności od typu pakietu rozgłoszeniowego format danych może wyglądać różnie.
