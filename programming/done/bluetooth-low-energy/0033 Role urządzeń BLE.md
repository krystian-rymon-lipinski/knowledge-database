### Role urządzeń BLE
Dopuszczalnym jest, aby jedno urządzenie spełniało kilka ról jednocześnie. Np. telefon może być urządzeniem centralnym dla czujnika i jednocześnie peryferyjnym dla innego telefonu.

###### Transmiter
Rola nastawiona wyłącznie na transmisję. Urządzenie pracujące w taki sposób nie zamierza nawiązywać połączenia z żadnym innym - wysyła tylko w przestrzeń dane rozgłoszeniowe dla obserwatorów.

###### Obserwator
Rola nastawiona wyłącznie na odbiór. Urządzenie pracujące w taki sposób nie zamierza nawiązywać połączenia z żadnym innym - odbiera tylko dane rozgłoszeniowe od transmiterów.

###### Urządzenie centralne
Rola pozwalająca tworzyć połączenia z innymi urządzeniami. To urządzenie centralne inicjuje połączenie i pozwala peryferjnym dołączyć do sieci.
Wymaga stosunkowo dużej mocy obliczeniowej i pamięci. Zazwyczaj przeznaczona dla urządzeń z ekranem dotykowym, gdzie łatwo można zaprezentować wykryte urządzenia peryferyjne oraz manipulować stanami połączeń.

###### Urządzenie peryferyjne
Rola polegająca na wysyłaniu danych rozgłoszeniowych celem ich odkrycia przez urządzenie centralne i nawiązaniem przez niego połączenia. 
Nie wymaga wielkich nakładów mocy obliczeniowej ani pamięci. Zazwyczaj przeznaczona dla rozmaitych sensorów, mikroprocesorów, etc.

 Dodatkowo zdefiniowano [[0034 Tryby urządzeń BLE|tryby]] i [[Procedury urządzeń BLE|procedury]], które dokładniej określają możliwości urządzeń pracujących w określonych rolach.

---
#tech-area/bluetooth-low-energy 
