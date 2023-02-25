Biblioteka umożliwiająca konwertowanie obiektów języka Java/Kotlin na plik typu [[JSON]] i z powrotem.

```csharp
dependencies {
     implementation 'com.google.code.gson:gson:2.8.8' 
}
```

Użycie:

```kotlin
val dataToSerialize = listOf("hey", "whatever")
val gson = Gson()
val type = TypeToken<List<String>>() {} // pusta klasa anonimowa, której parametr T to typ obiektu, któy jest serializowany do JSON-a
val json: String = gson.toJson(dataToSerialize, type) // zserializowany obiekt
val dataRetrieved = gson.fromJson(json, type) // zdeserializowany obiekt
```



**Syntax:**
https://www.vogella.com/tutorials/JavaLibrary-Gson/article.html