**6-bajtowy unikalny identyfikator urządzenia BLE.** Akceptowalny format: "00:11:22:33:AA:BB".
Może być różnego rodzaju.

###### Public device address
Stały, niezmienny przez całe "życie" urządzenia adres nadany przez producenta. Musi zostać zarejestrowany w Urzędzie Rejestracyjnym [IEEE](https://en.wikipedia.org/wiki/Institute_of_Electrical_and_Electronics_Engineers). 
https://standards-oui.ieee.org/oui/oui.txt - lista company ID, które składają się na takie adresy.

###### Random device address
Adres, który może być zaprogramowany na stałe lub zmieniać się w trakcie pracy urządzenia.
Można zdefiniować dalsze jego typy.

- static - adres stały przez całe "życie" lub przynajmniej od włączenia do włączenia urządzenia; używany, gdy producent nie chce rejestrować urządzenia
- private resolvable - zmieniający się cały czas adres (specyfikacja zaleca co ok. 15 min.), by urządzenie było niemożliwe do śledzenia; generowany przy pomocy [[0074 Klucze bezpieczeństwa BLE|klucza identyfikującego]] i liczby losowej; odszyfrować mogą go tylko urządzenia [[Procedury bezpieczeństwa BLE|sparowane]], ponieważ otrzymały ów klucz
- private non-resolvable - zmieniający się losowo, niemożliwy do odszyfrowania dla nikogo adres; używany w przypadku [[BLE Beacon|beaconów]] (z którymi i tak nie można się łączyć), by uniemożliwić śledzenie, 

**Urządzenie musi posiadać _public address_ lub _random static address_!**
Adresy prywatne zapewniają jedynie dodatkowe zabezpieczenia - po ich odszyfrowaniu można się po prostu dostać do "głównego" adresu, czy to publicznego czy statycznego.

---
https://novelbits.io/bluetooth-address-privacy-ble/
#tech-area/bluetooth-low-energy 