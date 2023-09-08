up: [[Jetpack Compose]]
#status/1-in-progress
#tech-area/android/ui

7gcMsb@2Y549

Opiera się na [[Navigation Component]], ale są pewne istotne różnice.
Potrzebna jest dependencja:

```kotlin
implementation("androidx.navigation:navigation-compose:{latest_version}")
```

1) `NavController`
`rememberNavController()` - zapamiętuje obiekt przy pomocy `rememberSaveable`; zapamiętuje, co jest w backstacku i co powinno być akurat wyświetlone (jest na górze backstacka).

Każdy element backstacka to `NavBackStackEntry` i posiada swoje _destination_ `NavDestination`, które mają swoje _routes_ i _arguments_.

Musi być skojarzony z jednym i tylko jednym `NavHost`-em.

To on nawiguje do konkretnego route'a:
```kotlin
navController.navigate(screen.route) {
	/* NavOptionsBuilder */
}
```

`NavOptionsBuilder` pozwala ustawić opcje nawigowania, np. `launchSingleTop`, etc.

Stan backstacka trzyma się za pomocą: `currentBackStackEntryAsState()`.

2) `NavHost` - composable, który wyświetla aktualny węzeł grafu; odpowiednik `NavHostFragment`; 
W swoim konstruktorze zawiera `NavController` i `NavGraph`, łącząc je w ten sposób ze sobą.   
```kotlin
NavHost(  
    navController = navHostController,  
    startDestination = Overview.route,  
    modifier = Modifier.padding(innerPadding)  
) {  /* NavGraphBuilder, definiujący węzły grafu */
    composable(route = Overview.route) {  
	    /* NavBackStackEntry */
        Overview.screen  
    }  
    composable(route = Accounts.route) {  
        Accounts.screen  
    }  
    composable(route = Bills.route) {  
        Bills.screen  
    }  
}
```

Composable w builderze mogą definiować argumenty. Poza koniecznym zdefiniowanym klucza typu String (tu `stringKey`) oraz typu argumentu, można dodać dodatkowe info, takie jak: czy argument jest nullable, jaka jest jego domyślna wartość, etc. Słowem - wszystko, co definiuje NavArgumentBuilder.

```kotlin
composable(
	route = "route/{stringKey}" /* Trzeba podać klucz argumentu */
	arguments = listOf(
		navArgument(stringKey) { type = NavType.* } /* StringType, IntType, etc. */
	)
)
```

Aby z tych argumentów skorzystać, należy zaznaczyć w `route`, że należy podać argument poprzez oznaczenie `{argument}`. W ten sposób metoda `navigate` będzie go wymagać.

3) `NavGraph`

Każda destynacja navigation grafu ma swój _route_ - String, który definiuje ścieżkę do Composable'a. Każdy destynacja musi mieć unikalny _route_.

Graf można zbudować poprzez `NavGraphBuilder` dostępny jako lambda w `composable`.

---
Testowanie Compose Navigation:

```kotlin
androidTestImplementation("androidx.navigation:navigationtesting:$composeNavigationVersion")
```

- trzeba dodać [[Rules|rule]] - `createComposeRule()`; można na niej wywoływać `setContent`, tak jak w aktywności
- `TestNavHostController` - navController na potrzeby testów
- na rule można wywoływać metody sprawdzające content; wszelkie asercje powinny być poza klamrą `setContent`!

Można testować, co widać po konkretnych klikach nawigacyjnych (jakie node'y się wyświetlają). Albo można porównywać route'y destinations z aktualną górą backstacka.


---
Istnieją też [[głębokie linki]], które prowadzą do konkretnych miejsc w aplikacji. Taki link można udostępnić również innym aplikacjom poprzez [[intent filters]]:

```xml
<activity
	...
	<intent-filter>
		<action android:name="android.intent.action.VIEW" />
		<category android:name="android.intent.category.DEFAULT" />
		<category android:name="android.intent.category.BROWSABLE" />
		<data android:scheme="app_name" android:host="single_account" />
	</intent-filter>
</activity>
```

A w nawigacji można je ustawić w `composable`:

```kotlin
composable(
	route = SingleAccount.routeWithArgs,
	deepLinks = listOf(navDeepLink { 
		uriPattern = "app_name://route"
	)
)
```

Głębokie linki można testować, wpisując uriPattern w [[adb]].