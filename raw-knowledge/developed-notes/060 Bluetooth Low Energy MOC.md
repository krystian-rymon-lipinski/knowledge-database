**Technologia bezprzewodowej wymiany informacji między urządzeniami skupiona na jak najmniejszym poborze przez nich mocy.**

Oprogramowanie rozdzielone jest na trzech modułach:
- Kontroler
- Host
- Aplikacja

W przypadku niektórych implementacji (np. sensorów BLE) wszystkie te moduły przeliczane są przez jeden chip.

###### Warstwy stosu protokołów
- [[0065 Physical Layer|Physical Layer]] (Kontroler)
- [[0066 Link Layer|Link Layer]] (Kontroler)
- [[0069 Interfejs Kontroler-Host|Interfejs Kontroler-Host]] (*ang. Host-Controller Interface (HCI)*)

- [[006A L2CAP Layer|L2CAP layer]]
- [[006D ATT Layer|ATT Layer]]
- [[0073 Security Manager|Security Manager]]
- [[GATT Layer]]
- [[0078 GAP Layer|GAP Layer]]

---
Na przestrzeni kolejnych wersji poprawie ulegały różne stałe opisujące możliwości technologii. Wykaz zmian dostępny jest tu: [[BLE - Bluetooth 5.0 changes]].
Technologia ma swoje [[Ble Security Concerns|ryzyka bezpieczeństwa]].
Moje pytania odnośnie technologii: [[BLE - pytania]]

---
Characteristic format types - Assigned Numbers on Bluetooth SIG

https://infocenter.nordicsemi.com/index.jsp?topic=%2Fsds_s140%2Fdita_common%2Fglossary%2Fglossary.html&anchor=l2cap - wrzucić to do głównego pliku, może się przydać dla wielu rzeczy

#status/backlog 
#tech-area/bluetooth-low-energy 