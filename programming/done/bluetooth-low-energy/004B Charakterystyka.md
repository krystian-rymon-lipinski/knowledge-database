### Charakterystyka
**Struktura GATT definiująca użyteczne dane. Najczęściej jedna charakterystyka odpowiada jednej wielkości.**

Każda charakterystyka należy do [[004A Serwis|serwisu]], musi być jego częścią. A zatem definicja charakterystyki musi się zawierać wewnątrz definicji serwisu.

Na **definicję charakterystyki** składają się przynajmniej dwa atrybuty: jeden z nich jest jej deklaracją, a drugi zawiera użyteczne dane. (Ponadto charakterystyka może zawierać deskryptory.)

**Deklaracja charakterystyki** to atrybut o specjalnym typie (UUID: 0x2803). Wartością atrybutu są [[004C Właściwości charakterystyki GATT|właściwości charakterystyki]], adres atrybutu z danymi oraz UUID charakterystyki.

Atrybut z danymi jako swój typ zawiera UUID charakterystyki, a jego wartością może być cokolwiek, przedstawione w jednym z wielu [[0052 Format charakterystyki|formatów]].

---
#tech-area/bluetooth-low-energy 