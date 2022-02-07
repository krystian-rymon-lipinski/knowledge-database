### Dane inicjujące
**22 bajty** (obowiązkowe), które zawierają wszystkie informacje potrzebne do nawiązania [[Połączenie BLE|połączenia]].
Wysyłane w pakiecie rozgłoszeniowym przez urządzenie skanujące do rozgłaszającego się.

Każdy z pakietów inicjujących ma taki sam format danych inicjujących.

- Access Address (4 bajty) - ten sam, co w *headerze* każdego pakietu BLE
- CRC Init (3 bajty) - inicjalizacja przeliczenia CRC

- Window Size (1 bajt) - służy do wyliczenia **rozmiaru okna transmisji** (1.25 ms * window size)
- Window Offset (2 bajty) - służy do wyliczenia **przesunięcia okna transmisji** (1.25 ms * window offset); razem z rozmiarem okna służą do zapewnienia szerszego przedziału czasowego dla pierwszego *connection event* ustanawianego przez urządzenie nawiązujące połączenie

- Interwał (2 bajty) - służy do wyliczenia **interwału połączenia** (1.25 ms * interwał)
- Latency (2 bajty) - służy do ustawienia **Slave Latency** połączenia
- Timeout (2 bajty) - służy do wyliczenia **Supervision timeout** połączenia (10 ms * timeout )

- Channel Map (5 bajtów) - obrazuje, które kanały będą używane do transmisji danych; najmniej istotny bit opisuje kanał z indeksem 0; 0 oznacza kanał nieużywany, 1 - używany
- Hop (5 bitów)- służy do ustawienia wartości **Hop Increment** - losowej wartości z przedziału 5-16
- SCA (3 bity) - służy do ustawienia najgorszej możliwej dokładności zegara urządzenia nawiązującego połączenie

---
#tech-area/bluetooth-low-energy 




