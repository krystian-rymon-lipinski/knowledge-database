### Typy pakietu rozgłoszeniowego
**Pakiet rozgłoszeniowy może spełniać różne cele.  Jego *header* definiuje 4-bitowe pole, określające, po co został transmitowany.**

###### Rozgłoszeniowy
Definiuje [[0041 Typy rozgłaszania|typ rozgłaszania]] urządzenia.
- 0b0000 = ADV_IND
- 0b0001 = DIRECT_IND
- 0b0002 = ADV_NONCONN_IND
- 0b1100 = SCAN_IND

	*Dane:*
	- adres urządzenia rozgłaszającego (6 bajtów) 
	- [[0039 Dane rozgłoszeniowe|dane rozgłoszeniowe]] (0-31 bajtów)

###### Skanujący
Obsługuje przekazanie [[003B Scan Request|dodatkowego zapytania]].
- 0b0011 = SCAN_REQ - wysłanie zapytania przez skaner
- 0b0100 = SCAN_RSP - odpowiedź urządzenia rozgłaszającego (ma format zwykłego pakietu rozgłoszeniowego)

	*Dane:*
	- adres urządzenia skanującego (6 bajtów)
	- adres urządzenia rozgłaszającego (6 bajtów)

###### Inicjujący
- 0b0101 = CONNECT_IND - prośba o nawiązanie połączenia wysyłana przez urządzenie centralne (skanujące)

	*Dane:*
	- adres inicjatora połączenia - urządzenia skanującego (6 bajtów)
	- adres urządzenia rozgłaszającego (6 bajtów)
	- [[0040 Dane inicjujące|dane inicjujące]] (22 bajty)

---
#tech-area/bluetooth-low-energy 