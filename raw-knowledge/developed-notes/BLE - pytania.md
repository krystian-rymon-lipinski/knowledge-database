up: [[060 Bluetooth Low Energy MOC]]
#status/3-freezer 
#tech-area/bluetooth-low-energy  

3. Czy Obserwator (rola) może być w trybie non-discoverable? Ale on w ogóle nie nadaje, więc czy w jego przypadku można mówić o trybie?
4. Czy Obserwator zaakceptuje (przekaże dalej) dane rozgłoszeniowe o typie connectable? Skoro jest przeznaczony dla transmiterów, które *muszą* oznaczyć swoje pakiety jako non-connectable?
6. Jaka jest różnica między trybami Broadcast a Non-connectable?
7. Pakiet L2CAP - czy przy większych pakietach (przekraczających MTU) nie ma czegoś w stylu długości całego komunikatu? czy pierwszy pakiet z kilku składających się na jeden duży nie zawiera w payloadzie pola opisującego długość pakietu? a jeśli tak, to jak go odróżnić o jakiejś tam zwykłej danej? czy to już implementation-specific? że jeśli dostaje L2CAP dłuższą strukturę  to sam ogarnia?)
8. Pakiet ATT - co siedzi w headerze protokołu ATT?
9. Pakiet LL - co siedzi w headerze protokołu LL?
10. Security Manager - co dokładnie oznacza, że klucze są jednokierunkowe?
11. Po co jest GAP, skoro wszystkie role definiowane w LinkLayerze? Czy GAP wysyła jakieś pakiety niżej w stack, które przechodzą przez L2CAP i dochodzą do LL? Na przykład takie, które mówią o tym, żeby zmienić rolę urządzenia albo tryb?
12. W jaki sposób uwierzytelniać klucze podpisujące? Skąd odbiorca ma wiedzieć, że jest to urządzenie godne zaufania?
13. Jakie są charakterystyki w GAP Service? Poza Device Name i Appearance, czy jest coś jeszcze?
