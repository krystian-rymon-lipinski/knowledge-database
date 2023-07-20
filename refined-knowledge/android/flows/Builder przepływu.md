up: [[Przepływ]]

**Kotlin API udostępnia następujące metody tworzenia przepływów:**

- `flow` - tworzy przepływ zimny; wartości emitowane są do przepływu poprzez `emit(element: T)`; emiter nie może emitować wartości z innego kontekstu - wszystkie wartości generowane do przepływu muszą powstać wewnątrz bloku kodu tegoż przepływu
- `flowOf(vararg elements: T)` - tworzy taki sam przepływ zimny jak `flow`, który emituje wartości podane jako parametry
- `callbackFlow` - tworzy przepływ zimny, który może emitować wartości z innego kontekstu; dobrze go wykorzystywać, jeśli dane przychodzą z [[Callback (-)|callbacków]]
- `channelFlow` - tworzy przepływ zimny, który może emitować wartości z innego kontekstu
- [[StateFlow]] - tworzy przepływ gorący zdolny do trzymania stanu
- [ShareFlow](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-shared-flow/)- tworzy przepływ gorący 

Można przekształcić przepływ zimny w gorący poprzez `stateIn` lub `shareIn`.

