up: [[013.3 Retrofit MOC]]

**Obiekt [[POJO|POJO]] trzymający dane po stronie klienta na potrzeby komunikacji z serwerem. Zdefiniowanie [[Konwerter Retrofit|konwertera]] pozwoli na automatyczną transformację surowych danych w konkretnym formacie na obiekty i z powrotem poprzez serializację i deserializację.**

```kotlin
/* Przykład dla konwertera GSON */
data class NumberObject(  
      @SerializedName("name") val name: String,  
      @SerializedName("image") val imageUrl: String  
)
```