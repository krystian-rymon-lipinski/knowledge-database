up: [[090 Git MOC]]
#status/in-progress 
#tech-area/git 

Git nie zapisuje zmian między plikami, ale zapisuje pliki w ich różnych stanach po zmianach (tzw. snapshots).

**Wszystkie pliki zapisane w którymkolwiek snapshocie są określane jako śledzone, w przeciwieństwie do plików nieśledzonych (lub ignorowanych), o których git nic nie wie.**

Pliki śledzone mogą być w **trzech stanach** (skupienia): 
- zmodyfikowane - po prostu zmienione, bez żadnego wpływu na gita
- przygotowane *(ang. staged)* - przygotowane do zacommitowania
- zacommitowane - już bezpieczenie trzymane w lokalnej bazie repo

Stan każdego z plików można podejrzeć poprzez `git status` - zostaną pokazane pliki nowe (niespełniające kryteriów plików ingorowanych), zmodyfikowane oraz przygotowane do commitu.
Można też `git status -s`, wtedy wypisany jest trochę krótszy.

Wiążą się z trzema sekcjami projektu git:
- folder do pracy *(ang. working directory)* - aktualny stan projektu: pliki na konkretnym branchu i konkretnym commicie gotowe użytkowania i modyfikacji; zmienione pliki oznaczone są jako *not-staged*
- obszar przygotowany *(ang. staging area)* - tu siedzą wszystkie pliki oznaczone jako przygotowane
- .git folder (repozytorium) - to tutaj siedzą wszystkie skompresowane dane o commitach, metadane, itd.; właśnie ten folder zostaje pobrany podczas klonowania repo

Przejścia między sekcjami:
- folder -> obszar = `git add <path>`
- obszar -> repo = `git commit` - zacommitowanie przygotowanych do tego zmian
- folder -> repo = `git commit -a` - wszystkie zmodyfikowane pliki zostaną zacommitowane bez stage'owania

- pliki zmodyfikowane -> pliki niezmienione = `git restore <path>`
- plik staged -> plik unstaged (zmodyfikowany) = `git restore --staged <path>`
- plik nowy -> obszar = `git add <path>`
- plik usunięty -> obszar `git rm <path>` - zwykłe usunięcie pliku z folderu będzie się jawiło jako "not staged"; po `git rm` ta akcja repo będzie "staged"
- `git rm --cached <path` - żeby zostawić plik w repo, ale usunąć go z trackowania przez gita (żeby na przykład móc go dodać do ignorowanych)

---
Można dodać plik `.gitignore` - pozwala to automatycznie blokować dodawanie pewnych plików do śledzenia. Nie pokażą się one nawet przy wypisywaniu statusu repo. Można dodać [[Wzorce z symbolami wieloznacznymi|wzorce z symbolami wieloznacznymi]], żeby wykluczać całe rodziny plików lub folderów.

Lista przydatnych plików do ignorowania w zależności od typu projektu: https://github.com/github/gitignore.

Możliwe jest posiadanie większej ilości plików .gitignore w podfolderach repo. Każdy taki plik może rządzić jedynie na swoim poziomie i niżej.

---
`git diff` - żeby zobaczyć wszystkie unstaged zmiany; nie tylko listę plików, ale i ich wnętrze
`git diff --staged` - żenby zobaczyć wszystkie staged zmiany

`git commit` - żeby zacommitować zmiany; najpierw dostanie się prompta, żeby rzucić wiadomością commita (pusta nie przejdzie!)
`git commit -m <"message">` - zacommitowanie zmian z konkretną wiadomością
`git commit -a` - zacommitowanie wszystkich zmodyfikowanych plików (dodanie ich do staging area i zacomittowanie w jednej komendzie)
`git commit --amend` - żeby dodać zmiany do poprzedniego commita, np. dodać brakujące plliki; jeśli wołany jest amend bez żadnych zmian w staging area, wciąż można zmienić commit message; amend efektywnie ZASTĘPUJE pierwszy commit drugim, pierwszy nie pojawi się w repo już nigdy; dobrze to robić tylko dla niespushowanych jeszcze nigdzie branchy

---
`git log` - żeby zobaczyć historię WSZYSTKICH commitów dla danego brancha
Przydatne parametry:
`-<numer>` - pokazuje tylko ileś ostatnich commitów
`-p` - pokazuje dokładne różnice w plikach(z diffem)
`--stat` - żeby zobaczyć listę pllików, które zostaly zmienione
`--pretty` - żeby wypisać logi w innej formie (można użyteć `--prettty=format:"<format wiadomości>"`, gdzie można zażądać różnch zmiennych, np. %H to commit hash, a %an - author name, etc.)
`--graph` - pokazuje zależności między commitami
`--no-merges` - nie pokazuje mergów, tylko zwykłe commity

`--since<date>` - commity od określonej daty w formacie YYYY-MM-DD
`--until<date>` - commity do określonej daty w tym samym formacie

`--author<glob pattern>` - filtrowanie po autorze
`--grep<glob pattern>` - filtrowanie po commit message
Można dodać kilka instancji tych parametrów, wówczas jest to filtr OR. Po dodaniu `--all-match` zamienia się on w filtr AND.

`-- <path>` - commity, które zmieniły coś w podanej lokalizacji






