up: [[013.1 Junit MOC]]
#tech-area/junit 
#status/3-freezer

1) Potrzebna do testowania composables w izolacji. Alternatywą jest `createAndroidComposeRule`, która ma świadomość konkretnej aktywności.
```kotlin
@get:Rule  
val composeTestRule = createComposeRule()

@get:Rule  
val composeTestRule = createAndroidComposeRule<MainActivity>()
```

2) Potrzebna do każdego testu używającego hilta, żeby wygenerować komponent. Na samej regule można potem wywoływać dodatkowe metody, np. injectować coś.
```kotlin
@get:Rule(order = 0)
var hiltRule = HiltAndroidRule(this)
```

Musi być w każdym teście, który korzysta z HiltViewModelu (albo innych wstrzykwanych dependencji). Jest to najważniejsza reguła testu, dlatego właśnie musi być oznaczona poprzez `order = 0`. Nie może być definiowana na poziomie klasy bazowej dla testów, tylko w klasie konkretnego testu.

Klasa testów musi być ponadto oznaczona @HiltAndroidTest.

