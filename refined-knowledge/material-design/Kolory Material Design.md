up: [[Stylowanie Material Design]]

**W systemie Material Design każdy kolor składa się z palety tonów - 13 odcieni o różnym stopniu obecności światła (od białego (100) do czarnego (0)).** 

Na paletę kolorów aplikacji składają się:
- kolory akcentu (po 4 tony każdy):
	- Primary -> Primary, On Primary, Primary Container, On Primary Container
	- Secondary -> Secondary, On Secondary, Secondary Container, On Secondary Container
	- Tertiary - Tertiary, On Tertiary, Tertiary Container, On Tertiary Container
- kolory neutralne (8 + 4 tony)
	- Neutral (określający tła i powierzchnie)
		- Surface: Dim, (blank), Bright
		- Surface Container: Lowest, Low, (blank), High, Highest 
	- Neutral Variant -> On Surface, On Surface Variant, Outline, Outline Variant
- kolory dodatkowe
	- Error (4 tony) -> Error, On Error, Error Container, On Error Container
	- kolory własne, specyficzne dla produktu

Poprzez zdefiniowanie zależności między tonami, Material Design jest w stanie wygenerować całą paletę kolorów dla trybów jasnego i ciemnego na podstawie czterech wybranych barw (Primary, Secondary, Tertiary, Neutral). Udostępnia również [narzędzie](https://m3.material.io/theme-builder#/custom) umożliwiające testowanie wyglądu aplikacji dla różnych palet oraz eksportowanie ich w formacie odpowiednim dla różnych platform.

Tokeny kolorów palety oraz ich domyślne wartości można podejrzeć w [tabeli](https://m3.material.io/styles/color/the-color-system/tokens#7fd4440e-986d-443f-8b3a-4933bff16646).

Android 12 definiuje ponadto [kolory dynamiczne](https://m3.material.io/styles/color/dynamic-color/overview).