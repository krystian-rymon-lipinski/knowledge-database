- klucz tymczasowy (*ang. Short Term Key*) - klucz szyfrujący **pojedycze** połączenie między urządzeniami (przy procedurze parowania)
- klucz trwały (*ang. Long Term Key*) - klucz szyfrujący **wszystkie** połączenia między urządzeniami, dopóki są ze sobą **powiązane** (*ang. bonded*); trzymany razem z EDIV i Rand - dwoma wartościami, które umożliwiają identyfikację konkretnego urządzenia spośród wszystkich powiązanych 
- klucz identyfikujący (*ang. Indentity Resolving Key*)- wykorzystywany przy generowaniu i identyfikowaniu adresu typu *random private resolvable*
- klucz podpisujący (*ang. Connection Signature Resolving Key*) - klucz służący do podpisywania niezaszyfrowanych danych 

Klucze te są **jednokierunkowe** - przypisane do roli, dla której zostały wygenerowane. Jeśli urządzenie zmienia [[0033 Role urządzeń BLE|rolę]] z urządzenia centralnego na peryferyjne (lub odwrotnie), mechanizmy bezpieczeństwa nie będą miały zastosowania w kolejnych połączeniach - do momentu wygenerowania kolejnych kluczy przypisanych do nowej roli.

---
#tech-area/bluetooth-low-energy 