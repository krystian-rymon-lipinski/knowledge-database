### Operacje zapisu protokołu ATT
**Podczas operacji zapisu klient powinien dostarczyć poprawny typ oraz wartość atrybutu. W przeciwnym razie serwer nie będzie w stanie przetworzyć żądania i w odpowiedzi poinformuje o błędzie.**

- prośba zapisu - wysłanie wartości atrybutu i oczekiwanie na odpowiedź od serwera
- żądanie zapisu - wysłanie wartości atrybutu bez oczekiwania odpowiedzi, a więc i bez potwierdzenia, czy udało się ją zapisać
- podpisane żądanie zapisu - żądanie zapisu z dodatkowym zabezpieczeniem
- przygotowanie kolejki zapisu - dla wartości wykraczających poza długość pojedynczego pakietu można zakolejkować kilka próśb zapisu
- wykonanie kolejki zapisu - po przygowaniu wszystkich wiadomości składających się na jeden komunikat można je wysłać do serwera
---
#tech-area/bluetooth-low-energy 