up: [[Jetpack Compose]]

**Annotacja pozwalająca wyświetlić wynik funkcji komponowalnej (wygląd kompozycji) bez instalowania aplikacji na urządzeniu.** Można nią oznaczyć tylko funkcje komponowalne bez parametrów (albo z parametrami z wartościami domyślnymi). Po zbudowaniu projektu Android Studio wygeneruje okno podglądu obok.

Można oznaczyć więcej funkcji komponowalnych jako @Preview, wyświetlają się wtedy jeden pod drugim. Można również oznaczyć jedną funkcję komponowalną większą liczbą @Preview.

Można odpalić *preview* na fizycznym urządzeniu i zobaczyć element komponowalny w praktyce.

**Parametry annotacji:**
- `showBackground = true`
- `showSystemUi = true` - pokazuje pasek systemowy
- `name = "Preview Name"`
- `widthDp = 320` (lub inna dowolna szerokość)
- `heightDp = 640` (lub dowolna inna wysokość)
- `uiMode = UI_MODE_NIGHT_YES` (uprzednio należy zadać w _trzeba_ skorzystać z `isSystemInDarkTheme()`; jeśli ustawi się domyślnie false lub true, to tylko jeden tryb zostanie poprawnie pokazany na preview)