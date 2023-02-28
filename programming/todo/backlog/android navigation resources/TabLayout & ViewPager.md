Kombinacja elementów, które służą do zaimplementowania widoku z zakładkami. Każda z zakładek powiązana jest z jednym fragmentem, między którymi można przechodzić poprzez kilkanie w zakładki lub wykonanie [[android gestures|gestu]] "Swipe".

1) Zdefiniowanie elementów w XML-u
```xml
<!-- widok przechowujący wszystkie zakładki -->
<com.google.android.material.tabs.TabLayout  
    android:id="@+id/configure_tab_layout"  
    android:layout_width="match_parent"  
    android:layout_height="wrap_content"  
    app:tabMode="fixed">  <!-- dla ustalonej ilości zakładek -->
  
    <com.google.android.material.tabs.TabItem        
    android:layout_width="wrap_content"  
	android:layout_height="wrap_content" />  
  
    <com.google.android.material.tabs.TabItem        
    android:layout_width="wrap_content"  
	android:layout_height="wrap_content" />  
</com.google.android.material.tabs.TabLayout>  

<!-- widok przechowujący aktualnie widoczny fragment -->
<androidx.viewpager2.widget.ViewPager2
    android:id="@+id/configure_view_pager2"  
    android:layout_width="match_parent"  
    android:layout_height="match_parent" />
```

2) Ustawienie adaptera dla ViewPagera
```kotlin
scan_view_pager2.adapter = PagerAdapter()
...
private inner class PagerAdapter : FragmentStateAdapter(this) {  
    override fun getItemCount() = 2 // liczba tabów; nie musi być stała, może zależeć od np. załadowanych treści
  
    override fun createFragment(position: Int): Fragment {  
        return when (position) {  
            /* Tu zdefiniuj konkretne klasy fragmentów */
        }  
    }  
}
```

3) Powiązanie adaptera z TabLayoutem - poprzez TabLayoutMediator
```kotlin
TabLayoutMediator(scan_tab_layout, scan_view_pager2) { tab, position ->  
    tab.text = when (position) { 
        /* Tekst zakładki trzeba ustawić, nie wystarczy zrobić tego w XML-u */ 
    }  
}.attach()
```

---

- `view_pager2.registerOnPageChangeCallback()` - definiuje callback wywoływany w momencie zmiany widocznego fragmentu (w dowolny sposób, klik lub swipe)

**W momencie załadowania layoutu z View Pagerem utworzony zostanie tylko pierwszy fragment! Kolejne zostaną utworzone dopiero w momencie przejścia do nich!**


https://material.io/components/tabs#usage

#status/done  