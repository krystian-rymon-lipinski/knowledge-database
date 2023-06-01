up: [[000 HOME]]
#status/2-backlog
#tech-area/android

**System operacyjny dla urządzeń mobilnych.**
[[Android Project Setup]]
[[Manifest Permissions]]


**Android Core API:**
- [[0031 Menu|Menu]]
- [[0032 RecyclerView|RecyclerView]]
- [[005E Dialog|Dialog]]
- [[005D DialogFragment|DialogFragment]]
- [[TabLayout & ViewPager]]
- [[Usługi]]

**Wzorce architektoniczne:**
- Single Activity / Fragment-Based / Navigation-Based
- Multiple Activities
- Reactive Programming
- Clean Architecture
	- Presentation layer - activities, fragments, viewmodels, UI-related components)
	- Domain layer - interfaces/contracts for the repositories)
	- Data layer - data storage and retrieval; implementations of the domain layer interfaces
- Repository pattern - oddzielenie pobierania danych od zapytań o nie; trzeba napisać interfejs, który definiuje zapytania, jakie źródło danych musi być w stanie przerobić (dodanie nowej danej, usunięcie, pobranie info, etc.); dzięki temu można zmienić źródło danych (np. z lokalnej bazy danych na serwis internetowy REST API) i nie trzeba zmieniać żadnych zapytań, a jedynie zmienić implementację kontraktu; **jest to tak naprawdę Domain Layer w Clean Architecture**
- hexagonal architecture (?)
- Model-View-Controller
- [[Model-View-Presenter]]
- [[0056 Model-View-ViewModel]]
- Model-View-Intent





**Technologie:**
- [[BLE Android API]]

---
https://books.goalkicker.com/AndroidBook/