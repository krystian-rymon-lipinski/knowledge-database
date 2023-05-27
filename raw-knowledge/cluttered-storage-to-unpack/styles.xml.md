#tech-area/android/xml 
#status/3-freezer 

**All Android internal styles can be found at [http://developer.android.com/reference/android/R.style.html](http://developer.android.com/reference/android/R.style.html)**

Można zdefiniować jakiś styl androidowy poprzez:
`style="?android:attr/buttonBarButtonStyle"
W styles.xml taki styl można zdefiniować poprzez przeszukanie styli poprzez używany theme. Np. jeśli główny theme aplikacji to AppCompat, to style do poszczególnych elementów UI można znaleźć poprzez Widget.AppCompat.*


For `app` namespace you don't need to specify `app:<property name>`. Just `<property name>` is enough.

## For example

```xml
<style name="FabStyle" parent="Widget.Design.FloatingActionButton"> 
    <item name="android:layout_width">wrap_content</item>
    <item name="android:layout_height">wrap_content</item>
    <item name="android:layout_margin">16dp</item>
    <item name="backgroundTint">@color/accent</item>
</style>
```