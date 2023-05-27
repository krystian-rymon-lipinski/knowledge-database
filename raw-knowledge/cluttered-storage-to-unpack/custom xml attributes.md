#android/xml 
#status/3-freezer 

**Można sobie zdefiniować dodatkowe atrybuty dla widoków poprzez zdefiniowanie pliku attr.xml w paczce _values_**. 

```xml
<declare-styleable name="MainActionButton">  
    <attr name="isActionOn" format="boolean" />  
</declare-styleable>
```

I później można już w xmlu ustawiać te rzeczy, wystarczy dodać namespace:
xmlns:app="http://schemas.android.com/apk/res-auto"
Można też dodać swój namespace, gdzie po /apk/ wchodzi definicja custom layoutu. (**Ale w projektach Gradle nie powinno się tego robić, app namespace wystarcza i system sobie szuka jej później.**)

**Trzeba uważać przy zmianie nazwy atryutu, bo Android Studio może tego nie trackować!** (A później powstają błędy podczas linkowania w kompilowaniu.)

```kotlin
class MainActionButton(context: Context, attrs: AttributeSet) : ExtendedFloatingActionButton(context, attrs) {  
  
    companion object {  
        private val STATE_IS_ACTION_ON = intArrayOf(R.attr.is_action_on)  
    }  
    private var isActionOn = false  
  
    fun setIsActionOn(isActionOn: Boolean) {  
        this.isActionOn = isActionOn  
        refreshDrawableState()  
    }  
  
    override fun onCreateDrawableState(extraSpace: Int): IntArray {  
        val drawableState = super.onCreateDrawableState(extraSpace + 1)  
        if (isActionOn) {  
            mergeDrawableStates(drawableState, STATE_IS_ACTION_ON)  
        }  
        return drawableState  
    }  
}
```

https://stackoverflow.com/questions/26690688/android-selector-on-custom-view-attribute
https://stackoverflow.com/questions/32261221/how-to-programmatically-set-custom-attributes-of-custom-components