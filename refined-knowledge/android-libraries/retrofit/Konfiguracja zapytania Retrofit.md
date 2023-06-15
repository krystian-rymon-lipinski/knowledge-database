up: [[Wrapper HTTP]]

**Różne annotacje Retrofita pozwalają zdefiniować dodatkowe ustawienia zapytania HTTP.**

```kotlin
	/* Zapytanie z modyfikowalnym URL-em */
	@GET("relativeUrl/{id}")
	fun getSomethingThroughId(@Path("id") Int id) : Call<T>

	/* Zapytanie z parametrem */
	@GET("relativeUrl")  
	fun getSomethingByName(@Query("name") numberName: String) : Call<T>
	/* Alternatywa dla zahardkodowanego parametru */
	@GET("relativeUrl?name=someName")
	fun getSomethingByName() : Call<T>

	/* Zdefiniowanie obiektu do przesłania (tylko jeśli zdefiniowano konwerter!) */
	@POST("relativeUrl")
	fun creatrSomethingNew(@Body T newObject) : Call<T>

	/* Zdefiniowanie nowego endpointu, bez wykorzystywania baseUrl z obiektu Retrofit */
	@GET  
	fun getSomething(@Url url: String) : Call<T> // zawołanie dla "twardego" linku
}
```

Ponadto:
- `@QueryMap` - dla większej ilości parametrów zapytania
- `@FormUrlEncoded` - dla aktualizowania tylko części własności zasobu na serwerze (?); wówczas każdą parę klucz-wartość trzeba oznaczyć annotacją `@Field`, np. `@Field("field_name") fieldValue: String`
- `@Multipart` - dla wysyłania
- `@Headers` - headery HTML, np. authorization, Content-Type, etc.
- `@HeaderMap` - dla większej ilości headerów