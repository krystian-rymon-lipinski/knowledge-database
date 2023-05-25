up: [[013.1 Retrofit MOC]]

**Zamiana HTTP API na interfejs Java/Kotlin przy użyciu [[Annotacje|annotacji]].** Metody interfejsu powinny zwracać obiekt typu `Call<T>`, gdzie `T` jest typem obiektu [[POJO Retrofit|POJO Retrofit]], który będzie zwrócony przez serwer. Można również zażądać w to miejsce obiektu typu `Call<ResponseBody>` - wówczas przesłane zostaną surowe bajty.

Struktura zapytania na serwer musi mieć formę opisaną przez [[Interfejs REST HTTP|interfejs REST HTTP]]. Należy zdefiniować przynajmniej metodę i dokładny adres zasobu (_endpoint_). (Najczęściej bazowy URL zdefiniowany jest w [[Obiekt Retrofit|obiekcie Retrofit]], więc wystarczy zdefiniować względną ścieżkę na serwerze.) Istnieją możliwości dodatkowego [[Konfiguracja zapytania Retrofit|konfigurowania zapytania]].

```kotlin
interface HttpService {
	@GET("relativeUrl") 
	fun getSomething() : Call<T>
}
```

Zapytania można kolejkować lub wykonywać od razu poprzez odpowiednio `enqueue()/execute()`. W obu przypadkach należy zdefiniować implementację _callbacków_ dla sukcesu i niepowodzenia otrzymania odpowiedzi z serwera. 

```kotlin
val httpCall = httpService.getSomethingThroughId(200)
httpCall.enqueue(object : Callback<T> {  
    override fun onResponse(call: Call<T>?, response Response<T>?) {
	    val object = response.body() /* Dane przekonwertowane na obiekt o konkretnym typie */
    }
	override fun onFailure(call: Call<T>, throwable: Throwable) { }
}
```