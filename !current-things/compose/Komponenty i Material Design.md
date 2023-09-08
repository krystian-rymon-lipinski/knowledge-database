up: [[Jetpack Compose]]
#status/1-in-progress
#tech-area/android/ui

Generalnie w momencie tworzenia aplikacji Compose tworzona jest paczka ui.theme, która zawiera 4 pliki: Color.kt, Shape.kt, Theme.kt, Type.kt. Tam są zdefiniowane np. kolory do dark mode'u, główny motyw aplikacji (dziedziczący po MaterialTheme).

Najczęściej korzystanie z Material Design theme sprowadza się do owrapowania go w pliku `Theme.kt`:

```kotlin
@Composable
fun AppTheme(
	useDarkTheme: Boolean = isSystemInDarkTheme(),
	content: @Composable() () -> Unit
) {  
	MaterialTheme(
		colorScheme = colors,
		shapes = shapes
		typography = typography, 
		content = content
	)
}
```

Paletę kolorów Compose definiuje poprzez `lightColorScheme` i `darkColorScheme`, na którą składają się kolory zdefiniowane w pliku `Color.kt`.

Typografię Compose definiują style tekstów, zdefiniowane w pliku `Type.kt`. Można nadpisać każdy z 15 definiowanych przez typografię Material Design styli poprzez zmienienie każdego z parametrów jaki definiują. Można również zmienić go jednorazowo dla konkretnego elementu - wystarczy zawołać na stylu `.copy()` i zamienić konkretny parametr.
Można definiować własne czcionki w projekcie LUB skorzystać z `GoogleFont.Provider` i ściągać je w rzeczywistym czasie działania aplikacji - bez zwiększania objętości pliku .apk.

Kształty Compose definiuje poprzez `RoundedCornerShape` dla pięciu styli posiadających zaokrąglenia oraz dodatkowo `RectangleShape` i `CircleShape`. Można je nadpisywać w pliku `Shapes.kt`.


Wówczas aby skorzystać z elementów zdefiniowanych w Theme.kt wystarczy:

```kotlin
color = MaterialTheme.colorScheme.primary
fontSize = MaterialTheme.typography.titleLarge
shape = MaterialTheme.shapes.medium

/* Można tez kopiować style i lekko je zmieniając: */
style = MaterialTheme.typography.headlineMedium.copy(
	fontWeight = FontWeight.ExtraBold)
```

Ikonki są dostępne pod: `Icons.*.*` - są różne ich style, Rounded, FIlled, Default, etc. Jeśli trzeba więcej ikonek, trzeba dołożyć dependencję: 
``implementation "androidx.compose.material:material-icons-extended:$compose_version"
https://fonts.google.com/icons

```kotlin
Icon(  
    imageVector = Icons.Rounded.Window,  
    contentDescription = "windows_icon"  
)
```



Można rozszerzać zdefiniowane w MaterialDesign kolory, typografie, etc. poprzez:
```kotlin
val ColorScheme.dieAdvantage: Color  
    @Composable get() = 
    if (isSystemInDarkTheme()) dark_AdvantageGreen 
    else light_AdvantageGreen
```

Wówczas można się do tych elementów odwołać w taki sam sposób, poprzez MaterialDesign.colorScheme.*

---

Dla aplikacji mieszanej (XML i Compose) można definiować theme w dwóch miejscach - w themes.xml i Theme.kt. NIestety trzeba wówczas edytować je również w dwóch miejscach. Można sobie to ułatwić, korzystając z [migration guide](https://developer.android.com/jetpack/compose/designsystems/views-to-compose), który opiera się na wykorzystaniu [Theme adaptera](https://google.github.io/accompanist/themeadapter-material/). 

Theme zdefiniowany w Compose nie musi być podawany do manifestu - wystarczy owrapować nim główny element UI i to wystarczy.

W aplikacji, która nie jest Compose, można z palca zdefiniować paczkę ui/theme i zacząć definiować Theme Compose (np. powiązany z Material Design).

---


Każdemu [[Komponenty UI|komponentowi UI]] odpowiada jego własna funkcja komponowalna. Np. Text() lub Image(). Można wykorzystać komponenty Material Design lub definiować własne na podstawie API komponentów Androida, w zależności od konkretnej dependencji.
###### Przydatne funkcje komponowalne generujące komponenty
- `Surface` - powierzchnia, którą można pokolorować i ma swój Elevation
- `Text` - pole tekstowe
- `Icon` - ikonka
- `Spacer` - pusty layout generujący przerwę
- `Divider` - linia-przerywnik
- `CircularProgressIndicator` - kręcące się kółko, sygnalizujące ładowanie
- `CheckBox` - jaki jest, każdy widzi

- `Button`, `ElevatedButton`, `IconButton`
- `FloatingActionButton`
- `Card`
- `Scaffold` - podobno jakiś komponent, gdzie można zdefiniować osobno topBar i bottomBar, który może być czymkolwiek



