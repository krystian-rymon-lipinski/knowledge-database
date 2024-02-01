#status/0-revision-needed
#android/app-navigation #android/app-architecture #android/gradle-dependency

Służy do nawigowania po aplikacji. Pozwala na utworzenie grafu, którego wierzchołki są miejscami docelowymi aplikacji (aktywności, fragmenty). Każda aktywność może mieć tylko jeden graf, można co najwyżej zdefiniować akcję przejścia do innej, ale po wejściu do niej musi ona definiować swój własny graf.

Potrzebne dependencje:
```kotlin
//Basic functionality of the graph
implementation("androidx.navigation:navigation-fragment-ktx:$nav_version")
//What for?
implementation("androidx.navigation:navigation-ui-ktx:$nav_version") 
//What for?
implementation("androidx.navigation:navigation-dynamic-features-fragment:$nav_version")
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
W layoucie trzeba zdefiniować widok, który będzie odpowiedzialny za trzymanie poszczególnych zmieniających się fragmentów. **Trzeba dodać id (dowolne), name (klasę tego specjalnego Fragmentu) i plik xml nawigacji, który opisuje graf przejść.**
```xml
<androidx.fragment.app.FragmentContainerView  
	android:id="@+id/fragment_container" 
    android:name="androidx.navigation.fragment.NavHostFragment"
    app:navGraph="@navigation/main_navigation"
    app:defaultNavHost="true"  
    tools:layout="@layout/fragment_scan"/>
```

**Trzeba dodać bibliotekę z fragmentami, jeśłi jesxzce jej nie ma!**

3) NavController
To ta klasa ma za zadanie nawigować po fragmentach, cofać, brać z backstacka, etc.
```kotlin
val navFragment = supportFragmentManager.findFragmentById(R.id.main_fragment) as NavHostFragment  
val navController = navFragment.navController
```

Można z niego korzystać we wszystkich klasach widoków:
- [`Fragment.findNavController()`](https://developer.android.com/reference/kotlin/androidx/navigation/fragment/package-summary#(androidx.fragment.app.Fragment).findNavController())
- [`View.findNavController()`](https://developer.android.com/reference/kotlin/androidx/navigation/package-summary#%28android.view.View%29.findNavController%28%29)
- [`Activity.findNavController(viewId: Int)`](https://developer.android.com/reference/kotlin/androidx/navigation/package-summary#(android.app.Activity).findNavController(kotlin.Int))

---

Można powiązać NavController z elementami nawigacyjnymi UI: dolnymi nawigacjami, app barami, etc.

A) [[BottomNavigationView|BottomNavigationView]]
- id menuItema z menu.xml musi odpowiadać konkretnemu id fragmentu z grafu
- `NavigationUI.setupWithNavController(main_navigation, navController)` - za kulisami powoduje to setup onClickListenera i dodanie do niego metody `onNavDestinationSelected`
- `android:menuCategory="secondary"` - każdy MenuItem musi posiadać ten atrybut, by był dodawany do backstacka

---

Można przekazywać argumenty między fragmentami poprzez zdefiniowanie ich w grafie nawigacji:

```xml
<!-- do zdefiniowania we fragmencie, który ma ten argument otrzymać -->
<argument  
android:name="customId"  
app:argType="integer"  
android:defaultValue="-1" />
```
```kotlin
val bundle = bundleOf("customId" to 12)
findNavController().navigate(R.id.action_id, bundle)
...
val receivedArgs = arguments?.getInt("customId")
```

By upewnić się co do typów argumentów, można użyć [[066 Safe Args Gradle Plugin]].


Można również przekazywać argumenty między fragmentem a dialog fragmentem.

https://developer.android.com/guide/navigation/navigation-getting-started
https://developer.android.com/guide/navigation/navigation-programmatic