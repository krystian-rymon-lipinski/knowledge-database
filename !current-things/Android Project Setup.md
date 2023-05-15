up: [[010 Android MOC]]
#status/in-progress 
#tech-area/android 

1) Postawienie systemu kontroli wersji (raczej gita):
- [[Konfiguracja Gita|konfiguracja użytkownika w Git]]
- dodanie remote'a i powiązanie go z lokalnym repo projektu
- initial commit

2) Utworzenie pustego projektu w Android Studio
3) Setup Gradle
- skonfigurowanie [[Repozytoria Gradle|repozytoriów Gradle]] dla pluginów:
	- `google()`
	- `mavenCentral()`
	- `gradlePluginPortal()`
- dodanie [[Pluginy Gradle|pluginów Gradle]]
	- [[071 Android Gradle Plugin MOC]]
	- [[072 Kotlin Gradle Plugin MOC]]
	- `java` (dla pisania w Javie)
- skonfigurowanie repozytoriów Gradle dla [[Dependencje Gradle|dependencji]]
- dodanie View Bindingu poprzez:

```kotlin
buildFeatures {  
	viewBinding = true  
}  
```

- zbudowanie projektu
4) Powiązanie remote repo z [[080 CI-CD MOC]] - w zależności od tego, które CI/CD jest wykorzystywane.
	a) Jeżeli repo jest w githubie, to można dodać: Actions -> Android CI. Domyślnie będzie to przynajmniej budowało kod. Można później dodać rzeczy typu unit testy. 
	Pisane jest toto w yaml-u.

Ponadto, jeśli trzeba:
- dodanie innych modułów (np. bibliotek) w tym samym projekcie
	-> junit: testImplementation 'junit:junit:4.12'
	-> mockito: 
			testImplementation 'org.mockito:mockito-core:$version'
			testImplementation 'org.mockito.kotlin:mockito-kotlin:$version'
			testImplementation 'org.mockito:mockito-inline:2.13.0' - żeby można było mockować finalne klasy i metody
	-> espresso:
			androidTestImplementation 'androidx.test.ext:junit:1.1.3'  
			androidTestImplementation 'androidx.test.espresso:espresso-core:3.4.0'
- podpięcie submodułów gitowych pod moduł

Należy trzymać się [[Standardy wytwarzania oprogramowania|stanardów wytwarzania oprogramowania]].