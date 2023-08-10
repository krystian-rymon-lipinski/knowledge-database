up: [[012 Android Studio MOC]]

Można je sobie dodawać lub usuwać z pasków narzędzi, inny do nich dostęp jet poprzez: *View -> Tool Windows -> <potrzebne_narzędzie>*. Można zmieniać ich tryb wyświetlania na przypięte do paska, osobne okno, etc. 

###### Lista narzędzi
- commit 
- drzewko projektu
- lista stworzonych zakładek
- rezultaty wyszukiwania metody, klasy, etc. w projekcie
- informacje i logi procesu aktualnie odpalonej aplikacji (trzeba być połączonym po USB i zezwolić na debuggowanie USB na telefonie)
- informacje procesu odpalonego w trybie "Debug"
- problemy (błędy, warningy, typos, etc.) dla aktualnego pliku bądź dla całego projektu
- struktura (aktualnie otwartego pliku) - właściwości, metody, etc.
- serwisy (?)
- VCS - po integracji z remote repo można tu przeglądać historię, branche, commity, pushować, fetchować i robić to wszystko, co umożliwia VCS
- manager urządzeń - fizycznych i wirtualnych; to tuaj można utworzyć wirtualne urządzenie, by na nim odpalić emulator; **tutaj można też (dla Android 11+) sparować urządzenie, żeby debuggować je przez Wi-Fi zamiast po kablu (wymaga odblokowania "Wireless debugging" w developer options)**
- running devices - umożliwia [[phone mirroring]] two-way
- emulator (by odpalić aplikację na wirtualnym urządzeniu - przewaga jest taka, że może ono być dowolne)
- profiler - mierzenie zużycia pamięci, CPU, baterii i innych ważnych elementów urządzenia
- app inspection - **dla połączonego urządzenia!**; badanie bazy danych, wykorzystania sieci i zadań wykonywanych w tle
- layout inspector - **dla połączonego urządzenia!**; podgląd atrybutów dla poszczególnych elementów layoutu
- build - lista wykonywanych tasków gradle przy budowaniu projektu (oraz błędy, jeśli coś poszło nie tak)
- warianty budowania -  definiowane są osobne zadania Gradle dla [[Warianty projektu Android|wariantów projektu]] i z tego narzędzia można ustawić, który wariant chcemy budować
- gradle - lista [[Zadania Gradle|zadań Gradle]] i [[Zadania Gradle AGP|zadań AGP]], które można wykonać dla całego projektu lub wybranych modułów
- eksplorator plików podłączonego urządzenia - przydatne, gdy trzeba podglądnąć np. jakiś plik konfiguracji tworzony poprzez SharedPreferences
- log wydarzeń - wydarzeń takich jak ukończony build, (nie)pomyślny push do remote repo, narzędzie (np. jakiś inspector) pracującty w tle
- hierarchia - klas lub metod (uwzględniająca te z bibliotek androida, a więc idąca do samego korzenia hierarchii)
- logcat - logi tego, co dzieje się na aktualnie połączonym urządzeniu
- **manager zasobów** - drawable, color, layout, etc,; dużo szybciej coś wyszukać stąd niż poprzez scrollowanie całej listy
- terminal
- TODO - lista rzeczy oznaczonych w kodzie jako //TODO