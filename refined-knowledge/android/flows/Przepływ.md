up: [[020 Kotlin MOC]]

**Przepływ _(ang. Flow)_ to strumień emitujący serie danych tego samego typu asynchronicznie, nie blokując głównego wątku, poprzez [[Korutyna|korutyny]]. Jest realizacją paradygmatu [[033 Programowanie reaktywne|programowania reaktywnego]].** Są tworzone przez różne [[Builder przepływu|buildery]].

- operatory pośrednie: `map`, `filter`, `take`, etc. - przekształcające strumień i/lub jego dane
- operatory kończące: `collect`, `single`, `reduce`, etc. - ich zachowanie zależy od typu przepływu:
	- dla przepływu zimnego - spowoduje wykonanie kodu zdefiniowanego w bloku przepływu (wyemitowanie wartości)
	- dla przepływu gorącego - spowoduje zasubskrybowanie konsumenta na przepływ, pozwalając mu przechwytywać emitowane wartości

`flowOn` zmienia _Dispatcher_, na którym wykonują się operacje zdefiniowane PRZED NIM. Wszystko co PO `flowOn` wykona się na _Dispatcherze_ zdefiniowanym w kontekście kolektora.

`distinctUntilChanged()` sprawdza, czy wartości w przepływie są takie same jak poprzednio. Jeśli tak - nie zostają one emitowane.

Do [[014 Android Testing|testów instrumentacyjnych]] (np. bazy danych Room) [dobrze jest](https://stackoverflow.com/questions/58589300/test-methods-of-room-dao-with-kotlin-coroutines-and-flow) korzystać z operatora kończącego `take(count: Int)`. Zwraca on przepływ z wybraną ilością elementów **oraz anuluje go po ich skonsumowaniu** (co zapobiega niekończącym się korutynom i w konsekwencji testom).
Alternatywą jest użycie biblioteki [[Turbine]].

---
https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-flow/
https://developer.android.com/kotlin/flow