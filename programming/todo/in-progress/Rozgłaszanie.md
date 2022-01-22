### Rozgłaszanie 
**Transmitowanie przez urządzenie Bluetooth LE wybranych przez siebie danych na [[Kanały BLE|kanale]] rozgłaszania z określoną częstotliwością w celu znalezienia odbiorcy.**

###### Dane niższych warstw protokołu
**2 bajty**, które zawierają ogólne informacje o rozgłaszanym pakiecie i są uzupełniane automatycznie:
- [[Typy pakietu rozgłaszania|typ]] danych rozgłoszeniowych (4 bity)
- TxAdd - typ adresu urządzenia rozgłaszającego; 1 dla przypadkowego, 0 dla publicznego (1 bit)
- RxAdd - typ adresu urządzenia docelowego; 1 dla przypadkowego,  0 dla publicznego (1 bit)
- długość danych urządzenia (6 bitów)

###### Dane urządzenia 
**6 bajtów** (obecnych zawsze) zawierających adres urządzenia rozgłaszającego.
**31 bajtów** (opcjonalnych), które zawierają istotne informacje podzielone na grupy.
Każda taka grupa składa się z:
- jej długości (1 bajt)
- jej [rodzaju](https://btprodspecificationrefs.blob.core.windows.net/assigned-numbers/Assigned%20Number%20Types/Generic%20Access%20Profile.pdf) - co opisuje dana grupa, np. 16-bitowe SIG serwisy albo nazwę urządzenia (1 bajt)
- danych (zmienna ilość bajtów)

Najczęściej spotykane rodzaje danych rozgłoszeniowych to nazwa urządzenia, UUID serwisów, [[0036 Flagi rozgłaszania|flagi]] i dane producenta.

Transmitowane przez urządzenie dane producenta mogą zostać przez niego ustandaryzowane, a ich znaczenie upublicznione - tak działają [[BLE Beacon|beacony]].

---
https://docs.silabs.com/bluetooth/latest/general/adv-and-scanning/bluetooth-adv-data-basics
#tech-area/bluetooth-low-energy 