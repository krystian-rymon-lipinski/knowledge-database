up: [[Jetpack Compose]]
#status/1-in-progress
#tech-area/android/ui

Można [różnie](https://developer.android.com/jetpack/compose/animation/introduction) wywoływać animacje:

- w modifierze: `animate*AsState` - Dp, Color, Float (np. alpha) - podaje się targetValue, a zmiana wartości z aktualnej w docelową jest rozciągnięta w czasie po jakiejś trajektorii (zależnej od typu animacji)
- w modifierze `animateContentSize` - dostosowuje rozmiar kontenera do treści w nim zawartej poprzez animację
- `AnimatedVisibility(booleanValue)` - animuje pojawianie się i znikanie komponentów; korzysta z EnterTransition i ExitTransition, by zdefiniować sposób pojawiania się i znikania elementów: np. Scroll_In/Out_Horizontally/Vertically, fadeIn/Out, expandIn, shrinkIn 
- `AnimatedContent(targetState)` - po czym targetState woła się when
- `updateTransition` - animowanie większej ilości rzeczy naraz - `Transition` trzeba podać docelowy stan, a później można już definiować poszczególne elementy poprzez `animate*` (np. Dp, Color, Float, Offset, Size, etc.)
- `rememberInfiniteTransition` - animacja powtarzająca się (też może więcej rzeczy naraz animować); 
- `Animatable` - najbardziej niskopoziomowe API; może korzystać z `pointerInput {}`, żeby reagować na [[android gestures|gesty]]

Można zdefiniować typ animacji poprzez parametr `animationSpec`:
- `spring` - mimickujący zachowanie sprężyny z konfigurowalnym współczynnikiem sprężystości oraz tłumieniem
- `tween` - można skonfigurować czas i opóźnienie animacji oraz jej szybkość na starcie i końcu (np. FastOutSlowInEasing)
- `infiniteRepeatable` - musi mieć zdefiniowaną wartość `animation`, np.:
```kotlin
animation = keyframes {
	durationMillis = 1000
	0.7f at 500
}
```
- `keyframes` - można też definiować `keyframes` od razu jako specyfikę animacji