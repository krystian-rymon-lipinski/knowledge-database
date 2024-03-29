up: [[Interfejs użytkownika]]
#status/4-liquid-nitrogen
#tech-area/design

**Narzędzie do projektowania UI/UX aplikacji.**
- UI = _[[Interfejs użytkownika|user interface]] = widok poszczególnych ekranów 
- UX = _user experience_ = logika przechodzenia między nimi

Figma wspiera [[120 Material Design|Material Design]]:
- [Material 3 Design Kit](https://www.figma.com/community/file/1035203688168086460) - lista [[Komponenty Material Design|komponentów]] wystylowanych zgodnie z wytycznymi Material3
- [Theme Builder](https://www.figma.com/community/plugin/1034969338659738588/Material-Theme-Builder) - plugin do testowania tworzenia palety [[Kolory Material Design|kolorów]] w zgodzie z wytycznymi Material3
- [Material Symbols](https://www.figma.com/community/plugin/1088610476491668236/Material-Symbols) - plugin do przeglądania [[Ikony Material Design|ikon Material Design]]


Warto zwrócić uwagę na plugin [[Relay]] - ułatwia on generowanie kodu bezpośrednio z designów. Choć na dziś (19.02.2024) jest wciąż w fazie wstępnej.


---

W przypadku tworzenia własnych elementów, kontenery dobrze jest tworzyć jako _frame'y_. Wówczas łatwo jest dodawać wewnątrz nich "rzeczywiste" elementy UI, takie jak tekst, kolory, etc.

**Można także tworzyć diagramy przypominające diagramy UML, przydatne przy planowaniu architektury aplikacji i zależności między poszczególnymi jej komponentami.** Aczkolwiek strzałki można tworzyć tylko zwykłe, co trochę uniemożliwia przedstawienie dokładnych relacji między obiektami.

Czasem trzeba się trochę namęczyć, żeby móc przerobić komponenty na własne potrzeby (_detach instance_, etc.).
