#android/xml 
#status/3-freezer 

drawable, dla którego można zdefiniować różne stany w zależności od czegoś

definiuje się je w osobnym xmlu:

```xml
<selector  
 xmlns:android="http://schemas.android.com/apk/res/android">  
  
 <item android:state_pressed="true"  
 android:color="@color/color_one" />  
  
 <item android:state_pressed="false"  
 android:color="@color/color_two" />  
  
</selector>
```
albo state_checked, zależy od elementu UI, który jest definiowany selektorem
albo state enabled, jeżeli to np. jakiś button

**Wówczas taki selector można zdefiniować jako np. backgroundTint i ma to wpływ na kolor!**