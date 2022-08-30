### Parametry rozgłaszania 
**Właściwości procesu rozgłaszania urządzenia, które można skonfigurować.**

###### Interwał rozgłaszania
Częstotliwość, z jaką urządzenie rozgłaszające transmituje pakiety rozgłaszania. Może przyjmować wartości **od 20 ms do 10.24 s z krokiem 0.625 ms**

Samo transmitowanie pakietu trwa tylko tyle, ile czasu na to fizycznie potrzeba (razy ilość kanałów). Później transmiter zostaje wyłączony do czasu rozpoczęcia kolejnego interwału.


###### [[0043 Kanały BLE|Kanały rozgłaszania]]
Urządzenie może zdecydować, na których kanałach trasmitować pakiety rozgłaszające - na wszystkich bądź tylko niektórych. W jednym interwale rozgłaszania zawiera się transmisja na wszystkich wybranych kanałach.


###### Czas rozgłaszania
Urządzenie może się rozgłaszać w nieskończoność (do momentu wyskanowania go i utworzenia z nim połączenia) lub przez określony czas, po którym przestaje transmitować pakiety rozgłaszania.

---
#tech-area/bluetooth-low-energy 
