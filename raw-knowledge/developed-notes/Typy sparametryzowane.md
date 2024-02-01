up: [[020 Kotlin MOC]]
#status/3-freezer 


Stosowane na przykład przy tablicach lub kolekcjach.

```kotlin
val t: Array<Int> /* Nie da się zapisać obiektów innego typu niż Int. */
val s: MutableSet<Ball> 
val l = listOf<String>() 
```

Obiekty są zapisywane i odczytywane jako typ, który deklaruje typ sparametryzowany.

```kotlin
class CustomList<T> /* Deklaracja klasy sparametryzowanej. T oznacza dowolny typ. */
class CustomList<T : Ball> /* T musi być typu Ball lub pochodną. */
val cl = CustomList<Volleyball>() /* Utworzenie obiektu klasy sparametryzowanej. */

fun <T> someFunction(t: T) /* Deklaracja funkcji sparametryzowanej. */
val obj = someFunction<Int>(10) /* Wywołanie funkcji sparametryzowanej. */
val obj2 = someFunction(10) /* Kompilator jest w stanie wywnioskować typ sparametryzowany po konstruktorze. */
```

Typ sparametryzowany może akceptować wartości puste.

```kotlin
fun <T> anotherFunction(t: T?) /* Wystarczy dodać ?, jak przy typie określonym */
```

Typ sparametryzowany domyślnie nie akceptuje typów pochodnych.

```kotlin
interface Dealer<T> /* Interfejs sparametryzowany. */
class VolleyballDealer: Dealer<Volleyball> /* Klasa implementująca interfejs sparametryzowany z konkretnym parametrem. */

val d1: Dealer<Volleyball> = VolleyballDealer() /* VolleyballDealer ma również typ Dealer<Volleyball>, bo polimorfizm, wszystko jest ok.*/
val d2: Dealer<Ball> = VolleyballDealer() /* VolleyballDealer nie ma typu Dealer<Ball> - to się nie skompiluje! */
```

Aby temu zapobiec, można jawnie zdefiniować typ sparametryzowany akceptujący typy pochodne. Wówczas nazywa się go **kowariantnym** - akceptującym typy pochodne tam, gdzie oczekuje się typu bazowego.

```kotlin
interface Dealer<out T>
val d1: Dealer<Volleyball> = VolleyballDealer() /* Wciąż OK. */
val d2: Dealer<Ball> = VolleyballDealer() /* Tym razem też okej. d2 jest typu Dealer<Ball>, ale też Dealer<T extends Ball>, jakby to powiedziała Java*/
val d3: Dealer<Volleyball> = BallDealer() /* Nie skompiluje się. Chcemy specyficznego typu, a dostajemy bazowy. */
```

Stosowanie typu kowariantnego: → jako wynik funkcji → jako argument funkcji (hence 'out', not 'in') → jako właściwość 'val' → jako właściwość 'var'

Istnieje również typ **kontrwariantny** - akceptujący typ bazowy tam, gdzie oczekiwany jest typ pochodny.

```kotlin
interface Dealer<in T: Ball>
val d3: Dealer<Volleyball> = BallDealer() /* Tym razem przejdzie, chcemy typu specyficznego lub jego typu bazowego. */
```

Stosowanie typu kontrawariantnego: → jako argument funkcji (hence 'in', not 'out') → nigdzie indziej!!!

Typ sparametryzowany może być lokalnie kowariantny/kontrawariantny - nie trzeba definiować tej jego właściwości globalnie - można na przykład tylko w konkretnym parametrze funkcji opatrzeć go słowem-kluczem 'in'.

Typ sparametryzowany nie poprzedzony 'in' ani 'out' jest **inwariantny** - akceptuje TYLKO referencje typu, które zostały mu zadeklarowane.