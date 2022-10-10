### Logical Link Control and Adaptation Protocol  (L2CAP) Layer
**Jego głównym zadaniem jest konwersja wiadomości z różnych protokołów wyższych warstw (poziomów abstrakcji) na wspólny format pakietu BLE oraz w drugą stronę.**

W praktyce oznacza to transformowanie wiadomości od protokołów:
- ATT (Attribute Protocol)
- SMP (Security Manager Protocol)
- jakikolwiek inny protokół, który definiuje wiadomości wyższego poziomu abstrakcji (np. LE Credit Based Flow Control Mode - transferowanie plików Over the Air lub tzw. [[Connection-oriented-channels]])


**Ponadto protokół ten odpowiada za fragmentację (w dół stosu protokołów) i rekombinację (w górę) pakietów większych niż maksymalny MTU.** Użytkownik na poziomie aplikacji może operować na strukturach dowolnej wielkości, zmiejszenie rozmiaru pakietu jest niezbędne dla niższych warstw stosu protokołów.

Protokół ten uszczegóławia [[006B Pakiet L2CAP|strukturę pakietu]] w porównaniu do niższych warstw protokołu.

---
#tech-area/bluetooth-low-energy 