up: [[0048 Struktury GATT]]

**Struktura GATT organizująca atrybuty opisujące powiązane ze sobą wielkości.**

**Deklaracja** serwisu zawiera:
- [[0053 Typ atrybutu ATT|typ atrybutu]] - UUID opisujące, czy serwis jest podstawowym lub drugorzędnym
- wartość atrybutu - UUID serwisu 

Serwis podstawowy zawiera funkcjonalności udostępniane przez urządzenie będące serwerem GATT.
Serwis drugorzędny może tylko modyfikować funkcjonalności serwisu podstawowego, sam z siebie nie ma celu (tego typu serwisy są raczej nieużywane).

Wewnątrz serwisu można również załączyć referencję (wskaźnik) do innego serwisu. Należy to zadeklarować atrybutem o specjalnym typie (UUID: 0x2802), gdzie wartość tegoż atrybutu zawiera UUID serwisu oraz adresy początku i końca definicji wskazywanego serwisu.