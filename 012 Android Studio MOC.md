up: [[000 HOME]]
#status/in-progress 
#tech-area/android/android-studio

**IDE (_ang. Integrated Developer Environment_) służące do tworzenia aplikacji mobilnych na Androida. Poza edytorem kodu ma wbudowane wiele innych funkcji, ułatwiających zarządzanie projektem programistycznym.**

- [[Widok okna Android Studio|widok okna Android Studio]]
- [[Narzędzia Android Studio|narzędzia Android Studio]]

...
- [[pluginy Android Studio]]
- [[skróty klawiszowe Android Studio]]


---
1. File
tworzenie projektów: nowy, importowany (z pliku), z repozytorium
tworzenie modułów: nowy, importowany (z plliku)
**można zaimportować sample project! np. zawierający bluetooth connectivity, jetpack compose lub runtime permissions handling**

otwieranie istniejących projektów (w tym ostatnich otwartych), zamykanie projektu (lub innych aktywnych projektów)
restartowanie, reindeksowanie, ponowne otwieranie, inwalidacja cashe, etc. - wszystko, co może pomóc, jeśli coś się zepsuło; + synchronizacja z Gradle

eksportowanie i importowanie ustawień IDE, powrót do domyślnych również

ustawienia
[[struktura projektu]]
2. Edit
znajdowanie/zastępowanie łańcuchów znaków; znajdowanie użyć metody, klasy, etc.
edycja pojedynczego miejsca kodu: 
rozszerzenie/skrócenie zaznaczenia, zmiana na wielką/małą literę, złączenie/zduplikowanie/sortowanie/odwrócenie kolejności linii, konwersja/dodanie/usunięcie wcięć
makra (?) i **zakładki (!)**
3. View
definicja, dokumentacja klasy/metody
ostatnie pliki, zmiany, lokacje
elementy edytora kodu: widoczne numery linii, wcięcia, ikony, ...

można zdefiniować soft-wrap, czyli po ilu znakach kod przechodzi do następnej linii
4. Navigation
Można nawigować do deklaracji, implementacji, wykorzystania, implementacji klasy nadrzędnej (super), testu.
Można nawigować po prostu wstecz i do przodu, do miejsca, w któym był kursor.
Można nawigować między błędami w otwartym aktualnie pliku.
Można nawigować do kolejnej i poprzedniej metody w pliku.
5. Generowanie kodu
Można wygenerować metody nadpisujące, implementujące, delegujące, konstruktory, equals(), hashCode(), toString(), test i copyright.
Można wygenerować różne template'y, np. metodę z parametrami albo pętlę for.
Można wygenerować komentarze.
Można przenosić linie oraz metody w dół/górę.
Można rozwijać/zwijać kod wewnątrz klamer - cały albo do któregoś poziomu.
Można ustawić autocompletion różnego typu.

**Code Inspection!** Po jego zleceniu pojawia się summary w narzędziu "Problems"
**Reformating file** - Code Cleanup, optymalizacja importów oraz przerw
Analiza dependencji i przepływu danych.

6. Refactor
Zmiana nazwy paczki/pliku/klasy, zmiana sygnatury klasy/metody.
Przenoszenie paczek.
Usuwanie nieużywanych resources. 

Migracja kodu do AppCompat/AndroidX (i inne migracje (np. JUnit 4.0 -> 5.0))
Dodanie Instant Apps Support lub RTL (right-to-left) support.
7. Build
Budowanie projektu/modułu.
Budowanie podpisanej/niepodpisanej paczki [[APK vs. AAB|.apk lub .aab]].
Budowanie konkretnego wariantu/typu/flavoru projektu/modułu.
Analiza pliku .apk - z czego się składa: klasy, resources, biblioteki, inne. Oraz ile zajmuje, i ile jest wymagane do pobrania (bo te dwie liczby nie muszą się zgadzać).
Czyszczenie/rebudowanie projektu, odświeżanie zlinkowanych projektów C++.
Edytowanie wariantów, flavorów, bibliotek i dependencji.
8. Run
Odpalanie aplikacji: normalnie, z debuggerem, z profilerem (ktory analizuje reakcje z UI oraz zużycie CPU, pamięci i energii). Można ustawiać różne konfiguracje - np. czyścić logi przed każdym odpaleniem albo odpalać aplikację na kilku urządzeniach naraz.
Odpalanie testów z analizą pokrycia.
Zarządzanie debuggerowymi breakpointami.
Testy UI przez Espresso - nagrywanie i puszczanie.
9. Tools
Generowanie dokumentacji.
Dodatkowe narzędzia: App Links Assistant i Android Gradle Plugin Upgrade Assistant
Firebase! Można się logować i robić tam jakieś rzeczy.
Dużo konsol - IDE Scripting Console, JShell Console, Groovy Console, 
10. VCS
Pierwsza rzecz to utworzenie repozytorium z poziomu AS. Wówczas można robić wszystkie rzeczy gitowe: ustawiać remote'y, klonować, commitować, branchować, pushować/pullować (jeśli jest gdzie i skąd), mergować, tagować, przeglądać liste commitów, rebaseować, itd., itp.
11. Window
Możliwość ustawienia domyślnego layoutu i powrót do niego - chodzi o ustawienie konkretnych okien narzędzi, nie wybranych tabów.
Taby można przypinać i zamykać: wszystkie, nieprzypięte, na lewo/prawo od wybranej.
Możliwość otwierania większej ilości edytorów z tabami, splitowanie jednego na dwa lub więcej mniejszych. 
12. Help
Informacje o AS, IntelliJ, "What's new", licencje, "Getting started", feedback. 
Tip of the Day | Productivity Guide | Keyboard Shortcuts 
Pokaż plik z logami | Zbierz logi do analizy | Analiza zużycia pamięci AS
Usuwanie poprzednich wersji AS (z jej ustawieniami, itp.)

---
Przy robieniu layoutów:
Component Tree - można przenosić komponenty z rzeczy do rzeczy! Zamiast kopiować samodzielnie!

Palette - pokazuje różne kontenery i kontrolki UI! Również te, o których mogło się nie słyszeć!
