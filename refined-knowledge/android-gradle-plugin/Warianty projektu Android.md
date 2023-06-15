up: [[061 Android Gradle Plugin MOC]]

**Kombinacja [[Flavory projektu Android|flavoru]] i [[Typy buildu projektu Android|typu buildu]]. Każdy z elementów wariantu może definiować własny [[Zbiory źródeł|zbiór źródeł]] - osobne zasoby, manifest i kod źródłowy.

Zasoby podczas budowania wariantu są łączone (*ang. merged*) - najważniejsze są te z typu *buildu*, później z *flavoru*, a na koniec z domyślnego folderu *main*. **Można te zasoby nadpisywać.**

Mergowanie kodu źródłowego wygląda inaczej - nie ma domyślnej wersji w folderze *main*. Albo wszystkie flavory definiują swoją implementację konkretnego zachowania aplikacji - albo żaden z nich tego nie robi i wtedy można to zdefiniować w folderze *main*. **Nie ma nadpisywania!**

Mergowanie manifestów wygląda [jeszcze inaczej](https://developer.android.com/build/manage-manifests#merge-manifests).

Nazwa wariantu to <nazwa_flavoru><nazwa_build_typu>. Dla większej ilości grup *flavorów*, nazwa musi zawierać *flavor* z każdej grupy. Podgląd na wszystkie nazwy wariantów (i wybór, który budować) jest możliwy w [[Narzędzia Android Studio|narzędziu Android Studio]]: warianty *buildu*.

Każdy wariant projektu można zainstalować na urządzeniu poprzez zadanie `install<variant_name>`. Tworzenie plików wykonywalnych jest możliwe na kilka sposobów:
- `assemble` - dla wszystkich wariantów 
- `assemble<variant_name>` - dla wybranego wariantu
- `assemble<build_type_name>` - dla wszystkich *flavorów* dla danego typu *buildu* 
- `assemble<flavor_name>` - dla wszystkich typów *buildu* dla danego flavoru


**Domyślnie zostaną utworzone warianty dla każdej możliwej kombinacji *flavoru* z typem *buildu***. Można blokować tworzenie niechcianych wariantów poprzez [filtr wariantów](https://developer.android.com/build/build-variants#filter-variants).

