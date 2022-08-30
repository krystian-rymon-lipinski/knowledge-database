### Kanały BLE
**40 częstotliwości**, na których transmitowane są wiadomości wysyłane przez urządzenia BLE.
Znajdują się w przedziale **2400 - 2480 MHz** (w przedziale [[ISM]]) z krokiem **2 MHz**.

###### Kanały rozgłaszania
Częstotliwości, na których transmitowane są **pakiety rozgłoszeniowe**. 
Oznaczone są indeksami: **37, 38, 39**.
Ich częstotliwości to odpowiednio: **2402, 2426, 2480 MHz**.

###### Kanały wymiany danych
Wszystkie pozostałe częstotliwości, służące do transmitowania **pakietów danych**.
Z każdym kolejnym *[[Połączenie BLE|connection event]]* kanał wymiany danych zmienia się wraz z formułą:
**new_channel = (current_channel + hop) mod 37**,
gdzie wartość *hop* zostaje przekazana w [[0040 Dane inicjujące|danych inicjujących]] podczas nawiązywania połączenia.

---
#tech-area/bluetooth-low-energy 
