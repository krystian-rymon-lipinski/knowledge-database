up: [[000 HOME]]
#status/in-progress 
#tech-area/git 
#environmental-variable

Jeden z **Systemów Kontroli Wersji** *(ang. Version Control System (VCS))*. Jest **narzędziem służącym do śledzenia zmian w plikach projektowych oraz ich zarządzaniem.** 

Jest to sytem typu DVCS *(ang. Distributed VCS)*, co oznacza, że każdy użytkownik posiada lokalnie kopię repozytorium trzymanego na serwerze i na tej lokalnej wersji może dokonywać wszelakich zmian (bez połączenia internetowego), a w razie chęci/potrzeby wrzucić na serwer swoje kontrybucje lub ściągnąć z niego zmiany dokonane przez innych twórców.


- [[Setup Gita|setup]]
- [[Konfiguracja Gita|konfiguracja]]

- [[Repozytoria Gita|repozytoria]]
- [[Gałęzie Gita|gałęzie]]
- [[Tagi Gita|tagi]]
- [[Aliasy Gita|aliasy]]

- [[Śledzenie zmian w Gicie|śledzenie zmian]]
- [[Historia commitów Gita|historia commitów]]
- [[Baza danych Gita|baza danych]]

- [[Łączenie gałęzi Gita|łączenie gałęzi]]
- [[Rebazowanie gałęzi Gita|rebazowanie gałęzi]]
- [[Flow gałęzi Gita|flow gałęzi]]


- [[Gitflows]]
- good git practices
	- annotated tags or lightweight tags?
	- rebase vs. merge - jak ważna jest historia projektu? czy powinna pokazywać wszystkie wzloty i upadki, czy może jednak dającą się prześledzić koherentną drogę od początku do końca?


---
- [[Serwer Gita]]
- [[Stashowanie gita]]
- [[Folder .git|folder .git]]
- [[Plik .gitignore|plik .gitignore]]
- submodules
- refspec
- git bisect

Dla projektu Androidowego większość operacji można dokonać z poziomu [[012 Android Studio MOC|Android Studio]] poprzez zakładkę **VCS**.

`git commit --amend` - żeby dodać zmiany do poprzedniego commita, np. dodać brakujące plliki; jeśli wołany jest amend bez żadnych zmian w staging area, wciąż można zmienić commit message; amend efektywnie ZASTĘPUJE pierwszy commit drugim, pierwszy nie pojawi się w repo już nigdy; dobrze to robić tylko dla niespushowanych jeszcze nigdzie branchy

`git reflog` - historia wkaźników branchy - gdzie były przez ostatnie kilka miesięcy (tylko branche lokalnego repo!)

`git show HEAD^` - pokaż przodka commita, na który wskazuje HEAD; można poprosić o drugiego przodka poprzez `^2` (tylko dla commitów, które są mergami)
`git show HEAD~` - też przodek commita, ale wgłąb; więc `~3` oznacza trzy commity wstecz od HEAD
Można te wywołania łączyć: `git show HEAD~3^2`.
**W niektórych terminalach ^ i ~ są znakami specjalnymi.** Wystarczy rzucić wskaźnik w cudzysłowach.


> [!NOTE] Przerobić
> https://git-scm.com/docs/gitcore-tutorial
> https://git-scm.com/book/en/v2

---
https://training.github.com/downloads/pl/github-git-cheat-sheet/
https://ndpsoftware.com/git-cheatsheet.html#loc=index
https://git-scm.com/book/en/v2
