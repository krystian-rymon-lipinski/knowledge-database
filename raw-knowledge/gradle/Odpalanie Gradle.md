up: [[070 Gradle MOC]]
#status/backlog 
#tech-area/gradle 

Trzeba zdefiniować zmienną środowiskową, która będzie brała odpowiednią wersję.
Najczęściej jest to (w Windowsie) `C:\Gradle\<numer_wersji>\bin`

```bash
gradle --version # wersja Gradle wykorzystywana przez system
gradle projects # struktura projektu Gradle; przydaje się zwłaszcza przy wielu subprojektach/modułach
```



> [!NOTE] Jak zmienić wersję Gradle?
> Taką, która pokazuje się `gradle --version`
