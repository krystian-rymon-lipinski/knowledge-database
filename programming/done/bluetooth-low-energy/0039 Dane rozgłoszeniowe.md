###### Dane rozgłoszeniowe
**31 bajtów** (opcjonalnych), które zawierają informacje o urządzeniu rozgłaszającym. Mogą one pomóc w zidentyfikowaniu go przez urządzenie skanujące. 

Są one podzielone na grupy, gdzie każda z nich składa się z:
- jej długości (1 bajt); **bajt opisujący długość nie wlicza się do samej długości**
- jej [rodzaju](https://btprodspecificationrefs.blob.core.windows.net/assigned-numbers/Assigned%20Number%20Types/Generic%20Access%20Profile.pdf) - co opisuje dana grupa, np. 16-bitowe SIG serwisy albo nazwę urządzenia (1 bajt)
- danych (zmienna ilość bajtów)

Najczęściej spotykane rodzaje danych rozgłoszeniowych to nazwa urządzenia, UUID serwisów, [[0036 Flagi rozgłaszania|flagi]] i dane producenta.

Transmitowane przez urządzenie dane producenta mogą zostać przez niego ustandaryzowane, a ich znaczenie upublicznione - tak działają [[BLE Beacon|beacony]].

---
https://docs.silabs.com/bluetooth/latest/general/adv-and-scanning/bluetooth-adv-data-basics
#tech-area/bluetooth-low-energy 