up: [[060 Gradle MOC]]
#status/4-liquid-nitrogen
#tech-area/gradle 
#environmental-variable 

Trzeba zdefiniować [[Zmienne środowiskowe|zmienną środowiskową]] `GRADLE_HOME`, która wskazuje na rozpakowany folder pobranej dystrybucji Gradle. Najczęściej jest to (w Windowsie) `C:\Gradle\<numer_wersji>`.
Ponadto trzeba dodać `bin` folder z tej dystrybucji do zmiennej `path`. Wówczas Gradle w tej wersji będzie się odpalało dla wszystkich komend `gradle`.

```bash
gradle --version # wersja Gradle wykorzystywana przez system
gradle projects # struktura projektu Gradle; przydaje się zwłaszcza przy wielu subprojektach/modułach
```
