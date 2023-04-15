#status/backlog  
#tech-area/standards

Implementacja:
- konwencja nazewnicza
- tabowanie (tabs vs. spaces)
- statyczna analiza kodu (automatyczna)
- analiza pamięciowo-czasowa kodu
	- narzędzie w AS do badania memory leaków i ogólnie zużycia pamięci
	- testy integracyjne na zrobienie N razy wyjątkowo ważnych algorytmów (i ewentualna próba ich usprawnienia)

Testy:
- jednostkowe
- automatyczne
	- integracyjne (operacje w aplikacji)
	- UI (przejście i klikanie w rzeczy)
	- fuzzy? (walidacja różnych inputów w aplikacji - trochę połączenie tych dwóch wyżej)
- regresyjne?
- smoke?

CI/CD
- gradle
- jenkins

---

# Project elements

1) Software Quality
	- clean code
	- refactoring
	- Lint / static code analysis
	- code review
2) Testing
	- unit testing
	- automated testing
	- manual testing
	- integration testing
	- fuzz testing (?)
3) CI/CD
	- continuous building
	- uploading app where it needs to go (Google Play Console)