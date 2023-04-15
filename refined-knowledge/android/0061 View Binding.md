up: [[0060 Kontrolowanie elementów UI]]
#status/revision-needed 

Kontrolowanie elementów UI w układach **poprzez wygenerowanie _binding class_ dla każdego układu**. Klasa taka posiada referencję do każdego elementu układu, który posiada atrybut *id* oraz do rodzica, wewnątrz którego zawiera się układ.

###### Setup
```groovy
android { /* W build.gradle dla modułu. */    
	buildFeatures { 
		viewBinding true    
	}  
}
```

Wówczas dla wszystkich układów z folderów *layout* wygeneruje się **binding class**. Można manualne oznaczyć te, dla których nie chcemy jej generować poprzez komendę *tools:viewBindingIgnore="true"* zdefiniowaną w układzie najwyżego poziomu (**root layout**).
Nazwa takiej klasy powstaje wskutek przetworzenia nazwy pliku .xml do [[konwecje nazewnicze|Pascal case]] i dodanie "Binding". Np. activity_main.xml -> ActivityMainBinding.class. Nazwy id zostają podobnie zmienione.

###### Używanie
```kotlin
binding = ActivityMainBinding.inflate(layoutInflater)
val view = binding.root
setContentView(view)  /* Dla aktywności. Dla innych Widoków będzie to wyglądało inaczej. */
...
binding.textId.text = "SomeText" /* Odwołanie się do TextView. */
binding.btnId.setOnClickListener(someListener) /* Ustawienie listenera na przycisku. */
```

**Inne możliwości:**

```kotlin
/* CustomView - można zdefiniować jako pole w klasie */	
val binding = CustomViewBinding.inflate(LayoutInflater.from(context), this, true)
/* RecyclerView - zmienna lokalna w onCreateViewHolder */
val binding = AdapterViewBinding.inflate(LayoutInflater.from(parent.context), parent, false)
return holder = ViewHolder(binding)
/* ViewHolder daje superklasie binding.root i może korzystać z bindingu */
```

**Jeśli layout jest zdefiniowany dla różnych konfiguracji, a któregoś z elementów UI nie ma na choćby jednym z nich, nie uda się go wygenerować!** Można to podejrzeć w wygenerowanej klasie:
```kotlin
/**  
 * This binding is not available in all configurations. * <p>  
 * Present:  
 * <ul>  
 *   <li>layout-sw600dp/</li>  
 * </ul>  
 *  
 * Absent: * <ul>  
 *   <li>layout/</li>  
 * </ul>  
 */
```

---

**Różnica między `inflate` i `bind`:**

- można zawołać `SomeBinding.inflate` - wówczas wygeneruje się hierarchia widoków poprzez `LayoutInflater.inflate()`, a za kulisami wywoła się `SomeBinding.bind`, które zwróci binding to tej hierarchii
- można też zawołać `SomeBinding.bind` - ale wówczas trzeba już mieć wygenerowaną hierarchię widoków, czy to przez `LayoutInflater.inflate()`, czy `setContentView`, etc.



https://developer.android.com/topic/libraries/view-binding#kts
#status/revision-needed