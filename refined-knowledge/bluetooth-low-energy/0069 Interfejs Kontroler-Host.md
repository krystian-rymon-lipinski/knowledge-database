up: [[050 Bluetooth Low Energy MOC]]

**Zestaw komend, formatów danych i innych procedur służących do wymiany informacji między Kontrolerem a Hostem.**

Na Kontroler narzucone są wymagania czasowe oraz jest odpowiedzialny za operowanie radiem - z tego powodu dobrze jest zaimplementować go na osobnym chipie.

Warstwy Hosta nie narzucają na niego wymagań. Definiują jednak bardziej złożone operacje, co sprawia, że ich implementacja zazwyczaj zawarta jest na bardziej zaawansowanym CPU.

Specyfikacja definiuje rozszerzenia interfejsu dla rozmaitych rodzajów połączeń (UART, USB, SDIO, etc.).