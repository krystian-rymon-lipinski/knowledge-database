https://material.io/components/tabs#usage


### TabLayout
Służy do przełączania między fragmentami. Klik działa normalnie na setOnClickListenera, ale można jeszcze swipe'ować.
Żeby ustawić te swipe'y, trzeba zasetupować ViewPager (ViewPager2, bo pierwszy jest w części deprecated).

ViewPager2 ma ma coś takiego jak OnPageChangeCallback.
view_pager2.registerOnPageChangeCallback()


1) Zdefiniowanie widoku - działa on trochę jak FrameLayout, jak widoczkiem, w który wpadają fragmenty.
<androidx.viewpager2.widget.ViewPager2  
    android:id="@+id/scan_view_pager2"  
    android:layout_width="match_parent"  
    android:layout_height="match_parent" />

2) Zasetupowanie adaptera, który umożliwi swipe'owanie między fragmentami.
```kotlin
scan_view_pager2.adapter = ScanPagerAdapter()
```

3) Zdefiniowanie tego adaptera
```kotlin
private inner class ScanPagerAdapter : FragmentStateAdapter(this) {  
    override fun getItemCount() = 2 // liczba tabów; nie musi być fixed
  
    override fun createFragment(position: Int): Fragment {  
        return when (position) {  
            0 -> ScannerFragment()  
            1 -> ActiveConnectionsFragment()  
            else -> ScannerFragment()  
        }  
    }  
}
```

4) Powiązanie adaptera z TabLayoutem - poprzez TabLayoutMediator
```kotlin
TabLayoutMediator(scan_tab_layout, scan_view_pager2) { tab, position ->  
    tab.text = when (position) {  /* text trzeba ustawić, nie wystarczy zrobić tego w XML-u */
        0 -> getString(R.string.tab_scanner_label)  
        1 -> getString(R.string.tab_connections_label)  
        else -> null  
    }  
}.attach()
```
