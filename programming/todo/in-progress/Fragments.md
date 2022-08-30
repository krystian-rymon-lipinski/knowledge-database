- trzeba rozszerzyć klasę fragment z biblioteki AndroidX (można z R.layout.x)
- supportFragmentManager pomaga robić rzeczy na fragmentach, znajdować po id, po tagach, ogarniać backstacki itd.
- żeby pokazać/zamieniać/usuwać fragmenty na ekranie, trzeba skorzystać z fragment transcations; każdą transakcję trzeba zacommitować

onCreateView służy do tego, żeby zinflate'ować główny widok fragmentu - żeby można było się dostać do jego podwidoków

```kotlin
override fun onCreateView(  
    inflater: LayoutInflater,  
    container: ViewGroup?,  
    savedInstanceState: Bundle?  
): View {  
    fragmentView = inflater.inflate(R.layout.fragment_scanned_devices, null)  
    return fragmentView   
}
```

Zamiast tego można wywołać konstruktor z parameterem:

```kotlin
class DemoFragment : Fragment(R.layout.fragment_demo)
```