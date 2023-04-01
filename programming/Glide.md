Biblioteka do przetwarzania zdjęć.

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