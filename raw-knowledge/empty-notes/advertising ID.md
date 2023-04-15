up: [[Określanie zawartości aplikacji w Google Store]]
#status/freezer 
#tech-area/android/google-play 


> [!NOTE] Jak to właściwie działa?



Jeśli aplikacja (lub któraś z jej bibliotek) jakoś przetwarza reklamy, należy wrzucić to w manifest:

```xml
<uses-permission android:name="com.google.android.gms.permission.AD_ID"/>
```