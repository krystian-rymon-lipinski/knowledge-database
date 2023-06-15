up: [[013.3 Retrofit MOC]]

**Obiekt definiujący podstawową konfigurację komunikacji sieciowej (przede wszystkim punkt wejścia do serwera i [[Konwerter Retrofit|konwerter]]) oraz tworzący [[Wrapper HTTP|serwis-interfejs HTTP]].**

```kotlin
val httpClient = Retrofit.Builder()
	.baseUrl("chosenUrl.com") // główny entry point serwera
	.addConvertedFactory(GsonConvertedFactory.create()) // konwerter dla biblioteki GSON; są różne konwertery, wybór konkretnego zależy od formatu danych przychodzących z serwera
	.build()
	
val httpService = httpClient.create(HttpService::class.java) // utworzenie serwisu

```