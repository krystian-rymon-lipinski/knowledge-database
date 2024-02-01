Typ obiektu, zawierający blok kodu. Można z nim zrobić dokładnie to samo, co z każdym innym obiektem - zapisać w zmiennej, podać jako parametr do funkcji, etc.

```kotlin
val someLambda = { x: Int -> x+5 } /* Wyrażenie lambda przypisane do zmiennej. Strzałka oddziela parametry od ciała. */
val lambdaResult = someLambda.invoke(10) /* Wywołanie lambdy, wynik to 15. */ 
val resultAgain = someLambda(10) /* Prostszy sposó wywołania lambdy. */
val somethingElse = someLambda /* To tylko przypisanie referencji do zmiennej, nie wykonanie czegokolwiek! */
```

Ostatnie przetworzone wyrażenie jest zwracane jako wynik wyrażenia lambda. Jeśli lambda nie ma parametrów, to '→' można pominąć.

```kotlin
val parameterlessLambda = { "Some string returned by lambda" }
val returnlessLambda: () -> Unit = { println("Some command to execute, since this lambda does not return shit. Or anything.") }
```

Typ wyrażenia lambda to **typ funkcyjny** - określa typy parametrów wejściowych i zwracaną wartość. Kompilator może się sam ich domyślić, ale można też zdefiniować je jawnie.

```kotlin
(parametry) -> typ_wyniku /* Typ wyrażenia lambda. */
val defaultLambda = { x: Int, y: Int -> x+y } /* Zwraca typ Int. */
val explicitLambda: (Long, Long) -> Long = { x, y -> x+y } /* Zwraca typ Long. */
```

Jeśli lambda ma pojedynczy parametr, można go zastąpić słowem 'it'.

```kotlin
val someLambda = { it + 5 } /* To się nie skompiluje! Kompilator nie wie, jakiego typu jest ten pojedynczy parametr! */
val someLambda: (Int) -> Int = { it + 5 } /* Teraz już wie, że do tego typu można dodawac liczby. */
```

Lambdę można przekazać do funkcji. Jest to wówczas funkcja wyższego rzędu.

```kotlin
fun highLevelFunction(number: Int, lambda: (Int) -> Int) {
	lambda.invoke(number) /* Wywołanie lambdy wewnątrz funkcji. */
}
someObject.highLevelFunction(10, { it * 30 })
someObject.highLevelFunction(20, { it + 10 }) /* Różne zachowania podane do tej samej funkcji. */
someObject.highLevelFunction(10) { it - 200} /* Lambda poza nawiasami funkcji! Dopuszczalne, jeśli jest ostatnim jej argumentem. */
```

Jeśli funkcja ma TYLKO lambdę jako argument, nie trzeba przy jej wywołaniu stosować nawiasów.

```kotlin
fun anotherHighLevelFunction(lambda: (Int) -> Int) { /* something here */ }
anotherObject.anotherHighLevelFunction { it - 10 } /* Bez nawiasów okrągłych. */
```

Funkcja może zwracać lambdę. Może też pobierać lambdę jako argument i zwracać lambdę jako swój wynik.

```kotlin
fun functionReturningLambda(number: Int) : (Int) -> Int { /* Typ funkcyjny (czyli lambda) jako typ zwracany przez funkcję. */ }
fun lambdaOverload(lambda: (Int) -> Int) : (Double) -> Double { /* Typ funkcyjny w parametrze i jako zwracana wartość. */ }  
```

Typ danych można określić nazwą zastępczą.
```kotlin
typealias DoubleTrouble = (Double) -> Double 
val lambda: DoubleTrouble = { it * 4.2 }
/* Kotlin nie wspiera aliasów lokalnych i zagnieżdżonych, tj. zadeklarowanych wewnątrz funkcji lub klasy! */
```