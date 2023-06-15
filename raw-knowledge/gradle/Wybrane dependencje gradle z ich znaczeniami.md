up: [[060 Gradle MOC]]
#status/3-freezer
#tech-area/gradle 

1) KTX
Rozszerzenia kotlinowe do rozmaitych bibliotek, wykorzystujące specyfikę języka (nazywane parametry, coroutinesy, etc.).
https://developer.android.com/kotlin/ktx

```kotlin
implementation "androidx.core:core-ktx:1.3.2" /* Wsparcie kotlinowe dla różnych paczek. */
implementation "androidx.fragment:fragment-ktx:1.5.5" /* Wsparcie kotlinowe dla API fragmentów. */
/* Etc., może być więcej takich rozszerzeń. */
```

**Nie trzeba definiować "zwykłej" biblioteki, ktx-y zawierają wszystkie funkcjonalności (niektóre i tak są pisane już w kotlinie i tak).**

2) 