Służy do nawigowania po aplikacji. Pozwala na utworzenie grafu, którego wierzchołki są miejscami docelowymi aplikacji (aktywności, fragmenty). Każda aktywność może mieć tylko jeden graf, można co najwyżej zdefiniować akcję przejścia do innej, ale po wejściu do niej musi ona definiować swój własny graf.

Potrzebne dependencje:
```kotlin
implementation "androidx.navigation:navigation-fragment-ktx:$nav_version"  
implementation "androidx.navigation:navigation-ui-ktx:$nav_version"  
implementation "androidx.navigation:navigation-dynamic-features-fragment:$nav_version"
```

1) Navigation Graph
Jest to nowy typ resources o typie Navigation. Każdy fragment ma swoje id, name i label (którą będzie widać po przejściu do niego).
```xml
<fragment  
    android:id="@+id/scanFragment"  
    android:name="com.siliconlabs.bledemo.home_screen.fragments.ScanFragment"  
    android:label="ScanFragment" >
    <action  
    android:id="@+id/action_configureFragment_to_deviceNameDialog"  
    app:destination="@id/deviceNameDialog" /> <!-- definicja przejścia do miejsca docelowego -->
    <action  
    android:id="@+id/action_deviceNameDialog_to_configureFragment"  
    app:popUpTo="@id/configureFragment" /> <!-- definicja przejścia w górę -->
</fragment>
```
`app:startNavigation="@id/start_fragment"` - pozwala ustawić pierwszy fragment po wejściu do komponentu z grafem
`<dialog>` - pozwala ustawić fragment jako widoczny jako dialog; oznacza to, że [[005D DialogFragment|DialogFragment]] również może należeć do grafu


2) NavHostFragment
W layoucie trzeba zdefiniować widok, który będzie odpowiedzialny za trzymanie poszczególnych zmieniających się fragmentów. 
```xml
<androidx.fragment.app.FragmentContainerView  
    android:name="androidx.navigation.fragment.NavHostFragment" <-- nazwa fragmentu -->
    app:navGraph="@navigation/main_navigation" <!-- graf związany z widokiem -->
    app:defaultNavHost="true"  
    tools:layout="@layout/fragment_scan"/>
```

3) NavController
To ta klasa ma za zadanie nawigować po fragmentach, cofać, brać z backstacka, etc.
```kotlin
val navFragment = supportFragmentManager.findFragmentById(R.id.main_fragment) as NavHostFragment  
val navController = navFragment.navController
```

---

Można powiązać NavController z elementami nawigacyjnymi UI: dolnymi nawigacjami, app barami, etc.

A) [[BottomNavigationView|BottomNavigationView]]
- id menuItema z menu.xml musi odpowiadać konkretnemu id fragmentu z grafu
- `NavigationUI.setupWithNavController(main_navigation, navController)` - za kulisami powoduje to setup onClickListenera i dodanie do niego metody `onNavDestinationSelected`
- `android:menuCategory="secondary"` - każdy MenuItem musi posiadać ten atrybut, by był dodawany do backstacka

---

Można przekazywać argumenty między fragmentami poprzez:
```kotlin
findNavController().currentBackStackEntry?.savedStateHandle?.getLiveData<FilterDeviceParams>(FilterFragment.FILTER_SETTINGS_KEY)?.observe(viewLifecycleOwner) {  
    // obserwacja zmiany
}
findNavController().previousBackStackEntry?.savedStateHandle?.set(
	FILTER_SETTINGS_KEY, prepareFilters()) //zapis wartości do przekazania
```

Można również przekazywać argumenty między fragmentem a dialog fragmentem.

https://developer.android.com/guide/navigation/navigation-getting-started
https://developer.android.com/guide/navigation/navigation-programmatic
#status/0-revision-needed 
#android/app-navigation 
#android/app-architecture 