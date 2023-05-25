up: [[013.1 Retrofit MOC]]
#android/gradle-dependency 

**Umożliwia automatyczną transformację surowych danych w konkretnym formacie na obiekty [[POJO Retrofit|POJO Retrofit]] i z powrotem poprzez serializację i deserializację.**

```kotlin
implementation("com.squareup.retrofit2:converter-gson:2.1.0") /* Konwerter dla biblioteki GSON
```

Zdefiniowane są dedykowane konwertery dla różnych bibliotek serializujących:
- [[GSON]]
- Jackson
- Moshi
- Protobuf
- Wire
- Simple XML
- JAXB
- Scalars

Konwerter można [konfigurować](https://futurestud.io/tutorials/retrofit-2-adding-customizing-the-gson-converter).