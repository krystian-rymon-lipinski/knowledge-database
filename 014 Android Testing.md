up: [[000 HOME]]

**Testy aplikacji Androidowych można podzielić na dwie grupy: lokalne oraz instrumentalne.** Android Studio dla każdej z nich definiuje ich własny [[Zbiory źródeł|zbiór źródeł]] oraz [[Konfiguracje dependencji Gradle|konfigurację dependencji]] do korzystania z bibliotek.

###### Testy lokalne

Odpalane są na maszynie programisty lub na serwerze odpowiedzialnym za automatyzację (narzędzie CI/CD). Są to [[Testy jednostkowe|testy jednostkowe]] (najczęściej) lub testy integracyjne niewymagające komponentów Androida (np. łączenie się z serwerem).


###### Testy instrumentacyjne  

Odpalane są na zewnętrznym urządzeniu z Androidem (telefonie, tablecie, etc.) lub w emulatorze. Są to albo [[Testy UI|testy UI]] albo [[Testy integracyjne|testy integracyjne]].

Foldery do plików źródłowych dla testów modułu zlokalizowane są pod ścieżką: `src/androidTest/`.
Korzystanie z bibliotek do testów instrumentacyjnych jest możliwe po dodaniu ich do projektu z konfiguracją `androidTestImplementation`.

[[Zadania Gradle AGP|Zadanie AGP]], które odpala testy instrumentacyjne to `connectedAndroidTest` (dla wszystkich wariantów).


