up: [[070 Gradle MOC]]

**Są to zewnętrzne biblioteki i moduły, które definiują przydatną dla projektu funkcjonalność.** Zamiast pisać ją na nowo, można użyć gotowego komponentu.

**Aby korzystać z dependencji należy najpierw zdefiniować [[Repozytoria Gradle|repozytoria]], z których Gradle będzie próbowało je znaleźć** *(ang. resolve)*. Można to zrobić poprzez:

- blok [[DependencyResolutionManagement]]
- blok `repositories { }`


Każda dependencja składa się z grupy, nazwy i wersji. Zmienne te można definiować w skrypcie na dwa sposoby:

```kotlin
dependencies { /* Blok do deklarowania dependencji */
	testImplementation("junit:junit:4.13.2")
	testImplementation(group="junit", name="junit", version="4.13.2")
} 
```

Należy również zdefiniować [[Konfiguracje dependencji Gradle|konfigurację dependencji]].
Dependencje mogą się okazać [[Dependencje tranzytywne|tranzytywne]], co może generować niepotrzebne zwiększanie rozmiaru projektu (i [[Rozmiar pliku .apk|pliku wykonywalnego]]) poprzez dodawanie nieużywanych modułów i klas.

---
Wyszukiwarka dependencji: https://search.maven.org/ -> https://central.sonatype.com/?smo=true