up: [[006A L2CAP Layer]]

**Zabiera z danych protokołowych [[0037 Pakiet BLE|pakietu BLE]] 4 bajty potrzebne na *header*.** W rezultacie taki pakiet składa się z:

- długości (2 bajty) - opisuje pole *channel ID* oraz właściwą treść komunikatu
- channel ID (2 bajty) - definiuje protokół wyższego poziomu, którego wiadomość jest transferowana na wspólny format; różne protokoły odznaczają się różnymi wartościami [[006C Kanały L2CAP|kanału]]
- treści komunikatu - pomniejszona o 4-bajtowy *header* składający się z powyższych pól wiadomość z prokołu leżącego wyżej na stosie protokołów