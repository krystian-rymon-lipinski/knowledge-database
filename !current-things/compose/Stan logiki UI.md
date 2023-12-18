up: [[Stan funkcji komponowalnych]]

**Całość _layoutu_ UI powinna być opisana stanem, który trzymany jest w funkcji komponowalnej na górze hierarchii.** Gdy staje się on bardziej złożony, dobrze jest wyłączyć go do osobnej klasy - [[Przechowalnik stanu logiki UI|przechowalnika]].

Najprościej jest korzystać z takiego _StateHoldera_ w taki sposób, że zapamiętuje się go w głównej funkcji komponowalnej poprzez `rememberSaveable {}` oraz `listSaver`, a wewnątrz niego trzymany jest sparcelowany stan poprzez `mutableStateOf()`.

```kotlin
@Composable
fun MainComposable() {
	...
	val stateHolder = rememberStateHolder(state = state)
}
...
@Composable  
fun rememberStateHolder(state: ComplexState) : ComplexStateHolder {  
    return rememberSaveable(saver = ComplexStateHolder.Saver) {  
        ComplexStateHolder(state = ComplexState())  
    }  
}
...
class ComplexStateHolder(state: ComplexState) {  
    var state by mutableStateOf(state)

	companion object {  
    val Saver: Saver<ComplexStateHolder, *> = listSaver(  
        save = { listOf(it.state) },  
        restore = { ComplexStateHolder(state = it[0]) }  
    )  
}
```
