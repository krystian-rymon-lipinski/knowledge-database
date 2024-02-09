up: [[016 Android Project Setup]]
#project-management 

**Kroki wspólne dla każdego nowego projektu Androidowego. Integrują narzędzia pozwalające rozwijać go w kontrolowanym środowisku, bazującym na iteracyjności i testowaniu.**

1) Utworzenie projektu w systemie zarządzającym
2) Utworzenie projektu w IDE
	- poprawne zbudowanie projektu
3) Postawienie systemu kontroli wersji (raczej gita): 
	- inicjalizacja lokalnego repozytorium
	- [[Konfiguracja Gita|konfiguracja użytkownika w Git]]
	- ustalenie [[Gitflows|flow projektu]] i [[Flow gałęzi Gita|flow gałęzi]]
	- postawienie zdalnego repozytorium na [[Serwer Gita|serwerze Gita]] (lub z wykorzystaniem [[Hostingi Gita|hostingu]]) i powiązanie go z lokalnym
	- _commit_ i _push_ wygenerowanych plików projektowych na zdalne repozytorium
	- dodanie pliku README.md
4) Dodanie automatyzacji poprzez narzędzia [[070 CI-CD MOC|CI/CD]]:
	- [[Continuous Integration|CI]] pipeline
	- [[Continuous Delivery|CD]] pipeline
		- dodanie pipeline'a do projektu
		- wygenerowanie klucza do podpisu i trzymanie go lokalnie w projekcie (zgodnie z lokalizacją w workflow!)
		- dodanie pliku keystore.properties lokalnie w projekcie (zgodnie z lokalizacją w workfklow!)
		- dodanie haseł do Google Play i kluczy na serwerze jako sekretów (keystore jako string base64)
		- dodanie signingConfig do build typu release
5) Setup Gradle
	- konwersja plików Gradle na DSL Kotlin (_.kts_)
	- dodanie suffixów dla różnych [[Typy buildu projektu Android|typów buildu]]
	**Wymaga podania paczki dla zasobów - w przeciwnym razie przy odpalaniu nie zostanie znaleziona główna aktywność, bo będzie zawierała w paczce również _suffix_.**
	
	```kotlin
kapt {  
	arguments {  
		arg("resourcePackageName", android.defaultConfig.applicationId ?: "default"
	}  
}
```

	- skonfigurowanie [[Repozytoria Gradle|repozytoriów Gradle]] dla pluginów:
		- `google()`
		- `mavenCentral()`
		- `gradlePluginPortal()`
	- dodanie [[Pluginy Gradle|pluginów Gradle]]: [[061 Android Gradle Plugin MOC|Android]], [[062 Kotlin Gradle Plugin|Kotlin]], [[063 Kapt Gradle Plugin|Kapt]]
	- skonfigurowanie repozytoriów Gradle dla [[Dependencje Gradle|dependencji]]
6) skonfigurowanie wstrzykiwania zależności
	- dodanie [[064 Hilt Android Gradle Plugin|gradle pluginu Hilt]]
	- dodanie [[013.8 Hilt|pozostałych rzeczy]]
7) Dodanie bibliotek Gradle do:
	- testów: [[013.1 Junit MOC|JUnit]], [[013.2 Mockito MOC|Mockito]], [[013.5 Espresso MOC|Espresso]]
	- logowania (np. [[013.4 Timber|Timber]])
	- [[0060 Kontrolowanie elementów UI|kontrolowania elementów UI]]
	- inne potencjalnie potrzebne ([[013.6 Room|Room]], [[013.3 Retrofit MOC|Retrofit]], [[GSON]], etc.)
8) Manifest
	- zasady Auto Backupu
