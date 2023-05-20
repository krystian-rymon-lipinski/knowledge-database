up: [[Gałęzie Gita]]

**Sposoby na zarządzanie gałęziami w repozytorium projektu, by ułatwić pracę wszystkim jego użytkownikom.**

###### 1. **Stabilność progresywna**
**Istnieje jedna gałąź (prawdopodobnie nazwana master), na której kod jest sprawdzony, przetestowany, stabilny i tylko stąd idzie do _releasu_.** Może istnieć kolejna gałąź, na której kod może być mniej stabilny, ale coś może już działać (np. develop), gdzie po dokładnych testach (albo przed/po _releasie_) można to _mergować_ do mastera. Reszta to gałęzie implementacyjne, gdzie kod nie musi być stabilny.

Liczba poziomów stabilności jest w zasadzie nieograniczona i zależy od wielkości projektu - w praktyce 2-3 powinny wystarczyć.

###### 2. Gałęzie tematyczne
**Dla każdej nowej funkcjonalności, _fixa_, etc. należy tworzyć osobną gałąź.** Pozwala to zamknąć konkretny problem w jego własnym kontekście, co pomaga podczas sprawdzania, testowania, _mergowania_ i innych rzeczy. Ponadto można powiązać ją z konkretnym _ticketem_ w systemie do śledzenia zadań.

###### 3. Przestrzenie nazw
Można grupować gałęzie ze względu na typ zadania, który wykonuje kod:
- feature/branch_name
- bugfix/branch_name
- improvement/branch_name

Dla projektów implementujących [[Gitflows|flow]] _intergration managera_, tenże manager może nadawać przestrzenie nazw w zależności od autora gałęzi:
- jm/branch_name - autor Juan Mendes
- ok/branch_name - autor Olga Kalinskaya, etc. 