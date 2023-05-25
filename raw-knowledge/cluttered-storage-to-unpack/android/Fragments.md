#status/freezer 
#tech-area/android 

**Nie można podawać żadnych parametrów w konstruktorze Fragmentu! FragmentManager nic o tym nie wie, więc przy odtwarzaniu go (np. przy zmianach orientacji lub jakiejkolwiek innej konfiguracji) i tak nie będzie o tym wiedział.**

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

---

_You'll notice that when a Fragment is detached, its onPause, onStop and onDestroyView methods are called only (in that order). On the other hand, when a Fragment is removed, its onPause, onStop, onDestroyView, onDestroy and onDetach methods are called (in that order). Similarly, when attaching, the Fragment's onCreateView, onStart and onResume methods are called only; and when adding, the Fragment's onAttach, onCreate, onCreateView, onStart and onResume methods are called (in that order)._ – Adil Hussain

Replace to remove + add, więc replacing też powoduje wywołanie *onDetach()* starego fragmentu i *onAttach()* nowego.

---

Czasem może być problem, żeby zareagować na onBackPressed(), zwłaszcza jeśli są nested fragmenty. Można wówczas wykorzystać callback: OnBackPressedCallback. Setupuje się go poprzez:
```kotlin
requireActivity().getOnBackPressedDispatcher().addCallback(this, callback)
```
I można ustawić flagę *isEnabled*, żeby decydować, czy wykonywać ten callback czy nie.