up: [[Jetpack Compose]]
#status/1-in-progress
#tech-area/android/ui

- `Column` - definiuje układ w orientacji pionowej
- `Row` - definiuje układ w orientacji poziomej
- `Box` - definiuje układ z nachodzącymi na siebie elementami
- `LazyColumn` - renderuje tylko elementy widoczne na ekranie - przydatne dla list pionowych; zawartość jest definiowana przez funkcję `items()`
- `LazyRow` - renderuje tylko elementy widoczne na ekranie - przydatne dla list poziomych; zawartość jest definiowana przez funkcję `items()`
- `LazyVerticalGrid`, `LazyHorizontalGrid` - siatka

Layouty Row i Column można pozycjonować poprzez:
- `Arrangement` - rozmieszenie elementów na głównej osi: poziomej dla `Row`, pionowej dla `Column`
- `Aligment` - rozmieszczenie elementów na prostopadłej osi

Istnieją różne wartości tych parametrów: `EqualWeight`, `SpaceBetween`, `SpaceAround`, `SpaceEvenly`, `End/Top`, `Center`, `Start/Bottom`

Layout Box można pozycjonować poprzez `Alignment`


Można zdefiniować custom `Arrangement` poprzez własną implementację:

```kotlin 
object TopWithFooter : Arrangement.Vertical {
	override fun Density.arrange(
		totalSize: Int,
		sizes: IntArray,
		outPositions: IntArray
	)
}
```

---
Layouty `Lazy` można wypełnić informacjami poprzez:
- `item()` - pojedynczy element, np. header
- `items()` - elementy listy
- `itemsIndexed` - elementy list z indeksem

Pamiętać jego stan można poprzez: `rememberLazy*State` (List, Grid, etc.). Wówczas można się odnieść o takich informacji jak:

```kotlin
val state = rememberLazyListState()
state.firstVisibleItemIndex
state.firstVisibleItemScrollOffset
state.layoutInfo.visibleItemsInfo
```

