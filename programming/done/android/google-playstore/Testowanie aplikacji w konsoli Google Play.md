**Możliwe jest udostępnienie paczki aplikacji do testowania z poziomu konsoli na trzy różne sposoby.

**Każdy nowa paczka udostępniona do testowania musi mieć nowy _code version_!** Później (po testach) można ją promować jako release przeznaczony na produkcję, nie trzeba tworzyć kopii releasu.

###### Testowanie wewnętrzne

1. Dodanie maila/maili testerów. Można też dodać jakieś miejsce (URL/mail), gdzie testerzy mogą dawać swój feedback.
2. Wygenerowanie linku i udostępnienie go testerom. Link trzeba odpalić będąc zalogowanym na konto Google, którego mail jest dodany w konsoli!
3. Wrzucenie paczki i wygenerowanie releasu oraz jego review - dokładnie taki sam algorytm postępowania jak dla releasu na produkcję.
4. Testowanie.
5. Promowanie releasu do testowania zamkniętego, otwartego lub od razu na produkcję.

###### Testowanie zamknięte

Można utworzyć ścieżki testowe "Alpha" i "Beta". Dla każdej z nich wygląda to podobnie.

1. Testerów można dodać tak samo jak dla testowania wewnętrznego, aczkolwiek można też dodać maile z "Grupy Google". Ponadto trzeba określić regiony dla których releasy dla testowania zamkniętego będą dostępne.
2. W porównaniu do testowania wewnętrznego można dodatkowo wygenerować link do strony aplikacji w Google Play na potrzeby zainstalowania wersji bezpośrednio na Androidowym telefonie.

Pozostałe punkty działają jak dla testowania wewnętrznego.

###### Testowanie otwarte

Po utworzeniu ścieżki wygląda to podobnie to testowania zamkniętego. Udostępnia się linki do strony internetowej lub strony aplikacji oraz trzeba zdefiniować dostępne regiony. Różnica polega na tym, że każdy z linkiem może odpalić wersję testową - nie ma żadnej listy maili, która weryfikuje testera, tak jak ma to miejsce przy testowaniu wewnętrznym czy zamkniętym. Można jedynie ograniczyć liczbę testerów (lub pozostawić ją nieograniczoną).

---
https://support.google.com/googleplay/android-developer/answer/9845334




