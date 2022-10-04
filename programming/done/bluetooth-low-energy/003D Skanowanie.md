### Skanowanie
**Nasłuchiwanie przez urządzenia Bluetooth LE [[0038 Pakiet rozgłoszeniowy BLE|pakietów rozgłoszeniowych]] na [[0043 Kanały BLE|kanałach rozgłaszania]] w celu odebrania danych od urządzenia rozgłaszającego i ewentualnego nawiązania z nim połączenia.**

**Interwał skanowania** definiuje częstotliwość wykonywania operacji skanowania.
**Okno skanowania** definiuje czas, w jakim odbiornik jest rzeczywiście włączony. Zawiera się wewnątrz interwału skanowania.

**Skanowanie może się odbywać tylko na jednym kanale na raz!** Nasłuchiwanie na kolejnym jest możliwe dopiero w kolejnym interwale! Jednakże rozgłaszające się urządzenie transmituje dane na wszystkich kanałach podczas jednego interwału rozgłaszania, więc nie jest to aż takim problemem.

Typy skanowania:
- pasywne - urządzenie nasłuchujące tylko odbiera pakiety rozgłoszeniowe
- aktywne - urządzenie nasłuchujące może wysłać do urządzenia rozgłaszającego [[003B Scan Request|dodatkowe zapytanie]]

---
#tech-area/bluetooth-low-energy 