up: [[016 Android Project Setup]]
#project-management 

**Kroki wspólne dla każdego nowego projektu Androidowego. Integrują narzędzia pozwalające rozwijać go w kontrolowanym środowisku, bazującym na iteracyjności i testowaniu.**

1) Utworzenie projektu w systemie zarządzającym
2) Utworzenie projektu w IDE
	- poprawne zbudowanie projektu
3) Postawienie systemu kontroli wersji (raczej gita): 
	- inicjalizacja lokalnego repo
	- [[Konfiguracja Gita|konfiguracja użytkownika w Git]]
	- ustalenie [[Gitflows|flow projektu]] i [[Flow gałęzi Gita|flow gałęzi]]
	- postawienie zdalnego repozytorium na [[Serwer Gita|serwerze Gita]] lub z wykorzystaniem [[Hostingi Gita|hostingu]]
	- _commit_ i _push_ wygenerowanych plików projektowych na zdalne repozytorium
	- dodanie pliku README.md
4) Dodanie automatyzacji poprzez narzędzia [[070 CI-CD MOC|CI/CD]]:
	- CI pipeline - na każdy commit oraz na PRy i merge do mastera:
		- poprawne zbudowanie projektu
		- przejście [[Testy jednostkowe|testów jednostkowych]]
		- przejście [[Testy integracyjne|testów integracyjnych]]
		- wygenerowanie pliku .apk
	- CD pipeline: upload do Google Play Store dla gałęzi releasowych
5) Setup Gradle
	- konwersja na plików Gradle na DSL Kotlin (_.kts_)
	- dodanie suffixów dla różnych [[Typy buildu projektu Android|typów buildu]]
	- skonfigurowanie [[Repozytoria Gradle|repozytoriów Gradle]] dla pluginów:
		- `google()`
		- `mavenCentral()`
		- `gradlePluginPortal()`
	- dodanie [[Pluginy Gradle|pluginów Gradle]]: [[061 Android Gradle Plugin MOC|Android]], [[062 Kotlin Gradle Plugin|Kotlin]], [[063 Kapt Gradle Plugin|Kapt]], [[064 Hilt Android Gradle Plugin|Hilt]]
	- skonfigurowanie repozytoriów Gradle dla [[Dependencje Gradle|dependencji]]
6) Dodanie bibliotek Gradle do:
	- wstrzykiwania zależności: [[013.8 Hilt|Hilt]]
	- testów: [[013.1 Junit MOC|JUnit]], [[013.2 Mockito MOC|Mockito]], [[013.5 Espresso MOC|Espresso]]
	- logowania (np. [[013.4 Timber|Timber]])
	- [[0060 Kontrolowanie elementów UI|kontrolowania elementów UI]]
	- inne potencjalnie potrzebne ([[013.6 Room|Room]], [[013.3 Retrofit MOC|Retrofit]], [[GSON]], etc.)
