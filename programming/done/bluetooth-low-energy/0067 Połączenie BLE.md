### Połączenie BLE
**Okresowa wymiana [[Pakiet danych BLE|pakietów danych]] między urządzeniem centralnym a peryferyjnym w ustalonych momentach w czasie i z określonymi [[003F Parametry połączenia BLE|parametrami]].** 

Aby nawiązać połączenie, urządzenie centralne wysyła pakiet rozgłoszeniowy o [[003C Typy pakietu rozgłoszeniowego|typie inicjującym]]. Jeśli urządzenie peryferyjne go odbierze i wyśle odpowiedź, połączenie można uznać za rozpoczęte. 

Wymiana danych jest realizowana na [[0043 Kanały BLE|kanałach wymiany danych]]. Dla każdego kolejnego interwału połączenia kanał ten zmienia się wraz z formułą:
**new_channel = (current_channel + hop) mod 37** (wynikiem jest indeks kanału),
gdzie wartość *hop* zostaje przekazana w inicjującym pakiecie rozgłoszeniowym podczas próby nawiązania połączenia.

Z początkiem każdego interwału połączenia radio urządzenia zostaje włączone, by dokonać wymiany danych - wysłania i/lub odebrania (*ang. connection event)*. Po jej zrealizowaniu **radio zostaje wyłączone do momentu rozpoczęcia kolejnego interwału połączenia**.

---
#tech-area/bluetooth-low-energy 