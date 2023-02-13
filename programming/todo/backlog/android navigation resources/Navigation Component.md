Służy do nawigowania po aplikacji. 
Potrzebne dependencje:
```kotlin
def nav_version = "2.3.0"
// Kotlin
implementation "androidx.navigation:navigation-fragment-ktx:$nav_version"  
implementation "androidx.navigation:navigation-ui-ktx:$nav_version"  
// Feature module Support  
implementation "androidx.navigation:navigation-dynamic-features-fragment:$nav_version"
```

Składa się z trzech komponentów:
1) Navigation Graph - ustawienie przejść między fragmentami/aktywnościami, etc.. Jest to nowy typ resources o typie Navigation.
Każdy fragment ma swoje id, name i label (którą będzie widać po przejściu do niego). Można też zdefiniować startDestination, wówczas ten fragment otworzy się pierwszy.

**Można dodać go jako <fragment> albo jako <dialog>!**

2) NavHostFragment
W layoucie trzeba zdefiniować widok, który będzie odpowiedzialny za trzymanie poszczególnych zmieniających się fragmentów. 
```xml
<androidx.fragment.app.FragmentContainerView  
    android:name="androidx.navigation.fragment.NavHostFragment"
    app:navGraph="@navigation/main_navigation"  
    app:defaultNavHost="true"  
    tools:layout="@layout/fragment_scan"/>
```
Trzeba zdefiniować nazwę fragmentu, który musi dziedziczyć po NavHostFragment.
Trzeba również powiązać graf z tym widokiem.
3) NavController
To ta klasa ma za zadanie nawigować po fragmentach, cofać, brać z backstacka, etc.

Można powiązać NavController z elementami nawigacyjnymi UI: dolnymi nawigacjami, app barami, etc.

A) BottomNavigationView
- id menuItema z menu.xml musi odpowiadać konkretnemu id fragmentu z grafu
- trzeba zawołać `setupWithNavController(main_navigation, navController);` za kulisami powoduje to setup onClickListenera i dodanie do niego metody `onNavDestinationSelected`
- każdy menuItem musi mieć `android:menuCategory="secondary"`, żeby każdy z nich dodawał się do backstacka i cofanie działało w porządku


```kotlin
findNavController().currentBackStackEntry?.savedStateHandle?.getLiveData<FilterDeviceParams>(FilterFragment.FILTER_SETTINGS_KEY)?.observe(viewLifecycleOwner) {  
    // obserwacja zmiany
}

findNavController().previousBackStackEntry?.savedStateHandle?.set(FILTER_SETTINGS_KEY, prepareFilters()) //zapis wartości do przekazania
```
Można przekazywać argumenty między fragmentami poprzez:



