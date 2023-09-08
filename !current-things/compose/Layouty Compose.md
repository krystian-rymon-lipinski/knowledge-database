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

Istnieją różne wartości tych parametrów: `EqualWeight`, `SpaceBetween`, `SpaceAround`, `SpaceEvenly`, `End/Top`, `Center`, `Start/Bottom`, `spaceBy(x.dp)`

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
Domyślnie stan każdego z elementów listy list skojarzony z jego pozycją. W ten sposób zmiana na liście (np. po usunięciu elementu) wpłynie na rekompozycję wszystkich zmieniających swoją pozycję elementów.
W to miejsce można zdefiniować inny klucz kojarzenia dla każdego elementu listy - np. jego id.
```kotlin
items(  
    items = data,  
    key = { it.id }  
) { task ->  
    /* ComposableComponent for each item */
}
```


- `itemsIndexed` - elementy list z indeksem

Pamiętać jego stan można poprzez: `rememberLazy*State` (List, Grid, Scaffold, etc.). Wówczas można się odnieść o takich informacji jak:

```kotlin
val state = rememberLazyListState()
state.firstVisibleItemIndex
state.firstVisibleItemScrollOffset
state.layoutInfo.visibleItemsInfo
```

**Ten stan nie odnosi się to samej zawartości (itemów) listy!**