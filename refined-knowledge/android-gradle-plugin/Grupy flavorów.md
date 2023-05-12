up: [[Flavory projektu Android]]

**Każdy *flavor* musi należeć do grupy.** Aby te grupy zdefiniować, należy dodać opisujące je nazwy do listy `flavorDimensions`. Kolejność ich podania jest jednocześnie ich hierarchią. Wpływa ona na:
- budowanie wariantu - *flavor* z najważniejszej grupy jest brany pod uwagę jako pierwszy podczas łączenia zasobów i konfiguracji
- nazwę wariantu - nazwa *flavoru* z grupy najważniejszej występuje w nazwie wariantu jako pierwsza

```kotlin
flavorDimensions += listOf("quickness", "thickness")

productFlavors {
	create("fast") {
		dimension = "quickness"
		...
	}
	create("slow") {
		dimension = "quickness"
		...
	}
	create("fat") {
		dimension = "thickness"
		...	
	}
	create("slim") {
		dimension = "thickness"
		...
	}
}
```

Większa ilość `flavorDimensions`, będzie prowadziła do jeszcze większej ilości możliwych wariantów. Dla powyższego przykładu oznacza to 4 warianty dla każdego z typów *buildów*:
- `fastFat<BuildType>`
- `fastSlim<BuildType`
- `slowFat<BuildType`
- `slowSlim<BuildType>`
