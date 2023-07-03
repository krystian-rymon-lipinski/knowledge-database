up: [[Architektura aplikacji Android]]
#status/1-in-progress
#tech-area/android

**Warstwa UI _(ang. UI layer)_ - warstwa mająca za zadanie przedstawienie informacji na ekranie poprzez [[Interfejs użytkownika|interfejs użytkownika]] oraz przechwytywanie _zdarzeń_ wygenerowanych przez użytkownika (interakcje z interfejsem poprzez [[android gestures|gesty]]) lub system (komunikaty o braku sieci, wyczerpującej się baterii, przychodzącym połączeniu, etc.).**

Składa się z następujących elementów:
- komponenty cyklu życia aplikacji ([[Activities|aktywności]], [[Fragments|fragmenty]]); każdy taki komponent ma swój widok, który organizuje elementy interfejsu użytkownika (rozmaite pola, teksty, checkboxy, etc.) prezentujące informacje
- modele przechowujące stan (np. MVVM) i udzielające go widokowi