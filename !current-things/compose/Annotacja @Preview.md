up: [[Jetpack Compose]]
#status/1-in-progress
#tech-area/android/ui

@Preview - annotacja pozwalająca podglądać wynik funkcji komponowalnych (UI) bez instalowania aplikacji na urządzeniu; można nią oznaczyć **tylko funkcje komponowalne bez parametrów**; po zbudowaniu projektu Android Studio wygeneruje okno podglądu obok

Można mieć więcej funkcji oznaczonych jako @Preview, wyświetlają się wtedy jeden pod drugim.
Można oznaczyć jednego composable'a większą ilością preview.

Można odpalić preview na fizycznym urządzeniu i zobaczyć element komponowalny w praktyce.
###### Przydatne parametry Preview
- `showBackground = true`
- `showSystemUi = true` - pokazuje pasek systemowy
- `name = "Preview Name"`
- `widthDp = 320` (lub inna dowolna szerokość)
- `heightDp = 640` (lub dowolna inna wysokość)
- `uiMode = UI_MODE_NIGHT_YES` (żeby działało, trzeba skorzystać z `isSystemInDarkTheme()`; jeśli ustawi się domyślnie false lub true, to tylko jeden tryb zostanie poprawnie pokazany na preview)
