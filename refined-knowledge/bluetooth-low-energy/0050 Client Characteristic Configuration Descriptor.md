up: [[004D Deskryptor]]

**Pozwala włączać i wyłączać przychodzenie notyfikacji z serwera.**
**UUID: 0x2902**

Na wartość deskryptora składają się dwa bajty. Pierwszy z nich odnosi się do komunikatów niewymagających potwierdzenia (_notifications_), drugi zaś do tych, których otrzymanie klient musi potwierdzić (_indications_). 

**Jedynka na wybranym bajcie oznacza możliwość otrzymywania konkretnego typu notyfikacji.**

Jeśli urządzenie spełnia rolę serwera GATT dla kilku urządzeń jednocześnie (np. przy wielu połączeniach), każdy klient będzie operował na swojej kopii wartości deskryptora. 