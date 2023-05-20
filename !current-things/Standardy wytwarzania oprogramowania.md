#status/backlog  
#tech-area/standards

Implementacja:
- konwencja nazewnicza
- [[style nazewnicze]]
- wiadomości commitów
	Here’s a model Git commit message: (https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)

```
Capitalized, short (50 chars or less) summary

More detailed explanatory text, if necessary.  Wrap it to about 72
characters or so.  In some contexts, the first line is treated as the
subject of an email and the rest of the text as the body.  The blank
line separating the summary from the body is critical (unless you omit
the body entirely); tools like rebase can get confused if you run the
two together.

Write your commit message in the imperative: "Fix bug" and not "Fixed bug"
or "Fixes bug."  This convention matches up with commit messages generated
by commands like git merge and git revert.

Further paragraphs come after blank lines.

- Bullet points are okay, too

- Typically a hyphen or asterisk is used for the bullet, followed by a
  single space, with blank lines in between, but conventions vary here

- Use a hanging indent
```
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
	- ograniczanie wielkości dependencji - jeśli jest potrzebna tylko drobna funkcjonalność, to można wyłączyć [[dependencja|dependencje]] tranzytywne; i w ogóle dobrze jest to kontrolować, zamiast bezmyślnie je tylko wrzucać
- jenkins

Issue Tracking

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