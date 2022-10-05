3. Czy Obserwator (rola) może być w trybie non-discoverable? Ale on w ogóle nie nadaje, więc czy w jego przypadku można mówić o trybie?
4. Czy Obserwator zaakceptuje (przekaże dalej) dane rozgłoszeniowe o typie connectable? Skoro jest przeznaczony dla transmiterów, które *muszą* oznaczyć swoje pakiety jako non-connectable?
6. Jaka jest różnica między trybami Broadcast a Non-connectable?
7. Pakiet L2CAP - czy przy większych pakietach (przekraczających MTU) nie ma czegoś w stylu długości całego komunikatu? czy pierwszy pakiet z kilku składających się na jeden duży nie zawiera w payloadzie pola opisującego długość pakietu? a jeśli tak, to jak go odróżnić o jakiejś tam zwykłej danej? czy to już implementation-specific? że jeśli dostaje L2CAP dłuższą strukturę  to sam ogarnia?)
