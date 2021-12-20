### Rozgłaszanie 

https://docs.silabs.com/bluetooth/latest/general/adv-and-scanning/bluetooth-adv-data-basics

31 bajtów, gdzie można wrzucać istotne informacje podzielone w pakietach.
Każdy taki pakiet składa się z:
- jego długości (1 bajt)
- flagi - co opisuje, np. 16-bitowe SIG serwisy albo nazwę urządzenia (1 bajt)
- dane (zmienna ilość bajtów)


Dane mogą być różnego rodzaju: https://btprodspecificationrefs.blob.core.windows.net/assigned-numbers/Assigned%20Number%20Types/Generic%20Access%20Profile.pdf
Najczęściej spotykane to complete local name, UUID services flags i manufacturer data.

Można zrobić extended advertising i wtedy ma się 1650 bajtów. 
Ale chyba jest to zbyt piękne, żeby nie miało jakichś drawbacks (poza pewnie ciągnięciem baterii jak szalone).


Można również ustandaryzować advertising data w specyfikacji, żeby rozgłaszać za każdym razem to samo.
Tak działają [[BLE beacons|beacony]].

---

#tech-area/bluetooth-low-energy 