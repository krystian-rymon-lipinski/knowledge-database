up: [[000 HOME]]

**Testy aplikacji Androidowych można podzielić na dwie grupy: lokalne oraz instrumentalne.** Android Studio dla każdej z nich definiuje ich własny [[Zbiory źródeł|zbiór źródeł]] oraz [[Konfiguracje dependencji Gradle|konfigurację dependencji]] do korzystania z bibliotek.

Odpalenie którychkolwiek testów spowoduje wygenerowanie rezultatów w postaci plików .xml. Można je podejrzeć w eksploratorze plików (Android Studio lubi te foldery chować) pod ścieżką `<module_name>/build/outputs` i `<module_name/build/results`. Ścieżkę tę można również podać w środowisku CI/CD, celem wygenerowania rezultatów testów jako artefaktów.

**Różne typy testów wymagają konkretnego [[Test Runner|test runnera]].**
**Zdarza się również, że trzeba użyć [[Rules|reguł testowych]].**

###### Testy lokalne

Odpalane są na maszynie programisty lub na serwerze odpowiedzialnym za automatyzację (narzędzie CI/CD). Są to [[Testy jednostkowe|testy jednostkowe]] (najczęściej) lub testy integracyjne niewymagające komponentów Androida (np. łączenie się z serwerem).

Foldery do plików źródłowych dla testów lokalnych są zlokalizowane pod ścieżką: `src/test/`.

###### Testy instrumentacyjne  

Odpalane są na zewnętrznym urządzeniu z Androidem (telefonie, tablecie, etc.) lub w [[Emulator Android Studio|emulatorze]]. Są to albo [[Testy UI|testy UI]] albo [[Testy integracyjne|testy integracyjne]].

**Jeżeli są odpalane na fizycznym urządzeniu, musi ono być włączone i odblokowane!**

Foldery do plików źródłowych dla testów instrumentacyjnych zlokalizowane są pod ścieżką: `src/androidTest/`.
Korzystanie z bibliotek do testów instrumentacyjnych jest możliwe po dodaniu ich do projektu z konfiguracją `androidTestImplementation`.

[[Zadania Gradle AGP|Zadanie AGP]], które odpala testy instrumentacyjne to `connectedAndroidTest` (dla wszystkich wariantów).

---
https://developer.android.com/training/testing/fundamentals/what-to-test
