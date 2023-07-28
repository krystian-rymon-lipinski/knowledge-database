up: [[000 HOME]]
#status/2-backlog
#tech-area/android
#tech-area/project-management

Należy trzymać się [[Standardy wytwarzania oprogramowania|stanardów wytwarzania oprogramowania]].

1) Utworzenie projektu w systemie DevOps
2) Postawienie systemu kontroli wersji (raczej gita): 
	- [[Konfiguracja Gita|konfiguracja użytkownika w Git]]
	- ustalenie [[Gitflows|git workflow]] i [[Gałęzie Gita|branch workflow]]
	- postawienie zdalnego repozytorium na [[Serwer Gita|serwerze Gita]] lub z wykorzystaniem [[Hostingi Gita|hostingu]]
3) Utworzenie projektu w Android Studio
	- zbudowanie projektu
	- initial commit i push na zdalne repozytorium
4) Setup Gradle
	- konwersja na plików Gradle na DSL Kotlin (.kts)
	- skonfigurowanie [[Repozytoria Gradle|repozytoriów Gradle]] dla pluginów:
		- `google()`
		- `mavenCentral()`
		- `gradlePluginPortal()`
	- dodanie [[Pluginy Gradle|pluginów Gradle]]: [[061 Android Gradle Plugin MOC|Android]], [[062 Kotlin Gradle Plugin|Kotlin]], [[063 Kapt Gradle Plugin|Kapt]], [[064 Hilt Android Gradle Plugin|Hilt]]
	- skonfigurowanie repozytoriów Gradle dla [[Dependencje Gradle|dependencji]]
	- dodanie suffixów dla różnych [[Typy buildu projektu Android|typów buildu]]
	- dodanie bibliotek testowych:

```kotlin
/* JUnit */
testImplementation 'junit:junit:4.12' 
/* Mockito */
testImplementation 'org.mockito:mockito-core:$version'
/* Trzeba dodać jeszcze MockMakera, żeby można było testować metody finalne */
/* Espresso */
androidTestImplementation 'androidx.test.ext:junit:1.1.3'  
androidTestImplementation 'androidx.test.espresso:espresso-core:3.4.0'
```

 - dodanie View Bindingu poprzez:

```kotlin
buildFeatures {  
	viewBinding = true  
}  
```


5) Dodanie automatyzacji poprzez narzędzia [[070 CI-CD MOC|CI/CD]]:
	- CI pipeline - na każdy commit oraz na PRy i merge do mastera:
		- poprawne zbudowanie projektu
		- przejście [[Testy jednostkowe|testów jednostkowych]]
		- przejście [[Testy integracyjne|testów integracyjnych]]
		- wygenerowanie pliku .apk
	- CD pipeline: upload do Google Play Store dla gałęzi releasowych
6) Dodanie dependencji [[013.8 Hilt|Hilta]]
7) Dodanie [[013.4 Timber|Timbera]] (albo innej biblioteki do logowania)
8) Przygotowanie [[110 UML|grafu use case'ów]] i [[Graf aplikacji|grafu aplikacji]]
9) Dodanie NavigationGraph do aplikacji

---