
Dopuszczalnym jest, aby jedno urządzenie spełniało kilka ról jednocześnie. Np. telefon może być urządzeniem centralnym dla czujnika i jednocześnie peryferyjnym dla innego telefonu.

###### Transmiter
Rola nastawiona wyłącznie na transmisję. Urządzenie pracujące w taki sposób nie zamierza nawiązywać połączenia z żadnym innym - wysyła tylko w przestrzeń dane rozgłoszeniowe dla obserwatorów.

###### Obserwator
Rola nastawiona wyłącznie na odbiór. Urządzenie pracujące w taki sposób nie zamierza nawiązywać połączenia z żadnym innym - skanuje tylko w poszukiwaniu danych rozgłoszeniowych od transmiterów.

###### Urządzenie peryferyjne (Slave)
Rola polegająca na wysyłaniu danych rozgłoszeniowych celem ich odkrycia przez urządzenie centralne i nawiązaniem przez niego połączenia - peryferyjne jedynie akceptuje chęć nawiązania połączenia.
Nie wymaga wielkich nakładów mocy obliczeniowej ani pamięci. Zazwyczaj przeznaczona dla rozmaitych sensorów, mikroprocesorów, etc.

###### Urządzenie centralne (Master)
Rola pozwalająca tworzyć połączenia z innymi urządzeniami. Urządzenie centralne skanuje w poszukiwaniu urządzeń rozgłaszających się i inicjuje połączenie z nimi połączenie. 
Wymaga stosunkowo dużej mocy obliczeniowej i pamięci. Zazwyczaj przeznaczona dla urządzeń z ekranem dotykowym, gdzie łatwo można zaprezentować wykryte urządzenia peryferyjne oraz manipulować stanami połączeń.

**Role Transmitera i Urządzenia Peryferyjnego korzystają z [[003A Rozgłaszanie|rozgłaszania]].**
**Role Obserwatora i Urządzenia Centralnego korzystają ze [[003D Skanowanie|skanowania]].**

Dodatkowo zdefiniowano [[0034 Tryby urządzeń BLE|tryby]] i [[0042 Procedury urządzeń BLE|procedury]], które dokładniej określają możliwości urządzeń pracujących w określonych rolach.

---
#tech-area/bluetooth-low-energy 
