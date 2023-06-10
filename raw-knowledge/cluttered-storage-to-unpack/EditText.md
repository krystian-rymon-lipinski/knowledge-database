#android/ui 
#status/3-freezer  

keyListener = DigitsKeyListener.getInstance("0123456789ABCDEFabcdef")  
setRawInputType(InputType.TYPE_CLASS_TEXT)

To spowoduje ustawianie hex values


Reakcja na zmianę napisu przed użytkownika:

```kotlin
editText?.addTextChangedListener (object : TextWatcher {  
    override fun beforeTextChanged(p0: CharSequence?, p1: Int, p2: Int, p3: Int) {}  
    override fun afterTextChanged(p0: Editable?) {}  
    override fun onTextChanged(p0: CharSequence?, p1: Int, p2: Int, p3: Int) {}  
})
```


