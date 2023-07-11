up: [[Architektura aplikacji Android]]
#status/1-in-progress
#tech-area/android

**Warstwa UI _(ang. UI layer)_ - warstwa mająca za zadanie przedstawienie informacji na ekranie poprzez [[Interfejs użytkownika|interfejs użytkownika]] oraz przechwytywanie _zdarzeń_ wygenerowanych przez użytkownika (interakcje z interfejsem poprzez [[android gestures|gesty]]) lub system (komunikaty o braku sieci, wyczerpującej się baterii, przychodzącym połączeniu, etc.).**

Składa się z następujących elementów:
- komponenty cyklu życia aplikacji ([[Activities|aktywności]], [[Fragments|fragmenty]]); każdy taki komponent ma swój widok, który organizuje elementy interfejsu użytkownika (rozmaite pola, teksty, checkboxy, etc.) prezentujące informacje
- modele przechowujące stan (np. MVVM) i udzielające go widokowi

---

UI elements + UI states = UI

UI state to data class, która zawiera w sobie wszystkie dane, które zawiera widok. Informacje dostaje on z data layer i przekształca na stan możliwy do wyświetlenia. UI state powinien być immutable i widokowi powinno się go podawać poprzez LiveData lub StateFlow.

Tych źródeł UI state może być więcej - zależy od tego, czy poszczególne dane są ze sobą powiązane. Jeśli nie, nie ma potrzeby wiązać ich w jedno ogrome skupisko danych, które będzie wymuszało na widoku aktualizację za każdym razem, gdy tylko cokolwiek się zmieni.

Przy większej ilości danych, ten problem i tak wystąpi - kontenery UI State będą coraz większe, a zmiana choć jednej z danych spowoduje odświeżenie wszystkich, co może potrwać. "This means that mitigation using the `Flow` APIs or methods like [`distinctUntilChanged()`](https://kotlin.github.io/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/distinct-until-changed.html) on the `LiveData` might be necessary."

Odbiorcą tych źródeł jest widok poprzez `observe` LiveData lub `collect` StateFlow. Odbiorcy powinny być zapięci na obserwowanie źródeł tylko tak długo jak one istnieją (czyli dopóki istnieje ViewModel, który jest emiterem). LiveData samo się o to troszczy, StateFlow trzeba samemu skonfigurować (najpewniej poprzez coroutines).

Źródła powinny też emitować info o ewentualnym ładowaniu lub błędach - dokładnie tak samo poprzez UI States.