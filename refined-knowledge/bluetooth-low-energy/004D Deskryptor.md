up: [[0048 Struktury GATT]]

**Struktura GATT zawierająca metadane, opisujące konkretną charakterystykę.**

Każdy deskryptor należy do [[004B Charakterystyka|charakterystyki]], musi być jego częścią. A zatem definicja deskryptora musi się zawierać wewnątrz definicji charakterystyki. 

**Deskryptory składają się tylko z jednego atrybutu!** 
Jego typem jest UUID deskryptora, a wartością cokolwiek, co ma być w nim zawarte.

**Jedyne dozwolone właściwości deskryptorów to zapis i odczyt!**

Najczęściej używane deskryptory SIG:
- [[004E Extended Properties Descriptor]]
- [[004F Characteristic User Description Descriptor]]
- **[[0050 Client Characteristic Configuration Descriptor]]**
- [[0051 Characteristic Presentation Format Descriptor]]