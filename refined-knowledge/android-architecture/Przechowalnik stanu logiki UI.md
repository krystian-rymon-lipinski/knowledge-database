up: [[Warstwa UI]]

**Komponenty UI wewnątrz widoku można zamieniać w zależności od np. parametrów ekranu urządzenia lub aktualnie pobranych danych (lub ich braku). Ponadto każdy z nich definiuje wiele własności składających się na jego stan - widoczność, tekst, marginesy, etc. - na które można wpływać z poziomu kodu.**

Logikę tych zachowań można pisać w klasie widoku, natomiast gdy staje się zbyt skomplikowana, dobrze ją przenieść do osobnej klasy - przechowalnika.

```kotlin
class AppState(val windowSizeClass: WindowSizeClass) {    
	val shouldShowBottomBar: Boolean        
	get() = windowSizeClass.widthSizeClass == WindowWidthSizeClass.Compact ||            windowSizeClass.heightSizeClass == WindowHeightSizeClass.Compact
	
	val shouldShowNavRail: Boolean
	get() = !shouldShowBottomBar
```