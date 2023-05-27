up: [[013 Android Libraries MOC]]
#android/gradle-dependency 
#status/3-freezer 

```groovy
implementation 'com.github.bumptech.glide:glide:4.15.1'
```

**Biblioteka do przetwarzania zdjęć.**

Przykład użycia: user wybiera jakieś zdjęcie poprzez ImageChooser (MediaPicker, etc.) i do aktywności zwracane jest Uri.
Wówczas:
```kotlin
Glide  
    .with(context)  
    .load(uri)  
    .centerCrop()  
    .placeholder(R.drawable.loading_spinner) /* W oczekiwaniu na załadowanie */
    .into(imageView)
```
Tada!
