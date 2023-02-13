Można animować poszczególne elementy grafiki wektorowej.


Wystarczy dodać do każdego elementu <path> atrybut name
```xml
<path  
    android:name="p-4"  
    android:pathData="M65.5706,54.8407C65.2108,54.8407 64.899,54.7207 64.5873,54.5527C62.7166,53.4727 60.8459,52.3927 58.9752,51.3127C57.7281,50.5927 57.5122,49.2726 58.5195,48.3606C59.0472,47.9046 59.7667,47.8086 60.4382,48.1686C61.6613,48.8406 62.8605,49.5606 64.0596,50.2567C64.8751,50.7127 65.6905,51.1687 66.4819,51.6727C67.1535,52.0807 67.4173,52.8727 67.2014,53.6167C67.0096,54.3127 66.2661,54.8407 65.5466,54.8407H65.5706Z"  
    android:fillColor="#A4C2D7"/>
```

Wówczas można się do niego odwołać w ten sposób:

```xml
<animated-vector xmlns:android="http://schemas.android.com/apk/res/android"  
    android:drawable="@drawable/redesign_ic_main_view_browser_scanning"  
    xmlns:aapt="http://schemas.android.com/aapt" >  
  <target      android:name="p-1"  
      android:animation="@animator/spinner_animation">  
      <aapt:attr name="android:animation">  
        <objectAnimator            android:startOffset="100"/>  
      </aapt:attr>  
  </target>
</animated-vector>
```
**Grafika wektorowa jest jednym plikiem, a odtwarzana na niej animacja odrębnym!** Aczkolwiek ten drugi również wchodzi w skład folderu drawable. 
