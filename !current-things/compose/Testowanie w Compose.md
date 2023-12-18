up: [[Jetpack Compose]]
X: [[013.5 Espresso MOC|Espresso]]
#status/1-in-progress
#tech-area/android/ui

**Chodzi o możliwość pisania testów UI, sprawdzających tworzenie funkcji komponowalnych.**

Potrzebne dependencje:
```kotlin
androidTestImplementation("androidx.compose.ui:ui-test-junit4")
/* Potrzebne do createAndroidComposableRule() */
debugImplementation("androidx.compose.ui:ui-test-manifest")
```

**ComposeTestRule** - [[Rules|rule]], potrzebna, by móc cokolwiek testować; są dwie opcje: `createComposeRule` lub `createAndroidComposeRule(Activity)`. Pierwsza pozwala testować elementy Compose w izolacji, druga w sprzężeniu z aktywnością.

```kotlin
@get:Rule  
val composeTestRule = createComposeRule()
```

Wówczas wystarczy na tej rule wywołać `setContent` (dokładnie ten sam, co przy `onCreate` aktywności) i już można wyświetlać funkcje komponowalne w teście. Reszta przydatnych do testów rzeczy (znajdowanie elementów UI, sprawdzanie ich własności, wykonywanie akcji) dzieje się również poprzez zdefiniowaną rule.

Najczęściej chodzi o:

```kotlin
composeTestRule.onNode* / composeTestRule.onAllNodes*
```

Można też zdefiniować flagę `useUnmergedTree` (domyślnie false), która definiuje, czy drzewo z węzłami powinno być mniej lub bardziej szczegółowe na potrzeby testów. Semantycznie np. IconButton jest jednym node'm, można go w testach rozdzielić na tekst i ikonkę, poprzez właśnie użycie niezmergowanego drzewa.

Wszystkie możliwe akcje definiuje [ta ściągawka](https://developer.android.com/jetpack/compose/testing-cheatsheet).


Można też przetestować zachowywanie stanu po [[Zmiany konfiguracyjne Android|zmianach konfiguracyjnych]].

```kotlin
val restorationTester = StateRestorationTester(composeTestRule)        restorationTester.setContent { MainScreen() }        restorationTester.emulateSavedInstanceStateRestore()
```


---
https://developer.android.com/jetpack/compose/testing