### Retrofit

biblioteka do REST API 
Można w nim zapiąć konwerter konkretnego parsowania obiektow typu JSON, np. GSON.

---
1) Utworzenie serwisu-interfejsu definiującego zapytania:

```kotlin
interface HttpService {
@GET("relativePath/{id}") // annotacja do metody
Call<T> getSomethingThroughId(@Path("id") Int id) //metoda do wykorzystania przez kod aplikacji 
@Query - dodatkowe opcje zapytania, np. sortowanie
}
```

Metoda zwraca obiekt typu call, który opakowuje obiekt otrzymany po konwersji z JSON-a.
2) Utworzenie obiektu typu Retrofit:
```kotlin
val httpClient = Retrofit.Builder()
	.baseUrl("chosenUrl.com") // strona, z której będzie się ściągało dane
	.addConvertedFactory(GsonConvertedFactory.create()) // konwerter obiektów JSON, tutaj konkretnie GSON
	.build()
val httpService = retrofit.create(HttpService::class.java)
```
3) Utworzenie klasy, która zamieni pola JSON-a na obiekt [[POJO]] w Androidzie. Zadzieje się to automatycznie przez wybrany konwerter.
```kotlin
class ReturnType {
	@SerializedName("id_from_json") 
	private val id: Int
}
```

4) Wywołanie serwisu
```kotlin
val httpCall = httpService.getSomethingThroughId(200)
httpCall.enqueue(new Callback<ReturnType) {
	override fun onResponse(response: Call<ReturnType>) { 
		val returnType: ReturnType = response.body() // żeby dostać obiekt z wrappera
	}
	override fun onFailure(call: Call>ReturnType>, throwable: Throwable)
}
```

Dependencje:
compile ‘com.squareup.retrofit2:retrofit:2.1.0’
compile ‘com.squareup.retrofit2:converter-gson:2.1.0’


https://square.github.io/retrofit/
https://medium.com/android-news/consuming-rest-api-using-retrofit-library-in-android-ed47aef01ecb
https://futurestud.io/tutorials/retrofit-2-adding-customizing-the-gson-converter