up: [[Jetpack Compose]]
#status/1-in-progress
#tech-area/android/ui

**Funkcje komponowalne _(ang. composable functions)_ - jakieś tam funkcje.**

Funkcje komponowalne można wywoływać tylko wewnątrz innych funkcji komponowalnych.
(Czy onCreate() jest funkcją komponowalną).

@Composable - annotacja do oznaczenia funkcji opisujących UI.

ComponentActivity()


Composables mogą zostać wywołane w dowolnej kolejności, równolegle, zostać pominięte lub być wywoływane bardzo często (za każdą zmianą stanu lub dla każdej klatki animacji).

Composable jest rekomponowany (wywoływany ponownie), gdy zmienią się jego parametry LUB gdy zmieni się wewnętrzy stan funkcji.