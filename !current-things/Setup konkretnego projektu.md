up: [[016 Android Project Setup]]
#status/2-backlog
#tech-area/project-management

**Pytania dotyczące architektury, na które lepiej (przynajmniej w części) odpowiedzieć sobie wcześniej, by później nie przerabiać projektu milion razy.**

- co ta aplikacja ma właściwie robić? jakie są jej feature'y
- zdefiniowanie architektury:
	- zdefiniowanie warstwy UI. **Dobrze jest przed startem projektu zdefiniować, ile będzie ekranów i co każdy z nich ma dokładnie robić.**
	- zdefiniowanie warstwy danych aplikacji - na jakich operuje, skąd je bierze, jak są ustrukturyzowane.

- przygotowanie [[110 UML|grafu use case'ów]] i [[Graf aplikacji|grafu aplikacji]]
	- zależności między klasami w kontekście Hilta


> [!NOTE] Ekrany
> "Define your screen as state in, events out"
It shouldn't care, where it gets the state from (ViewModel? StateHolder?). 
It also shouldn't care, who receives the events it puts out.
