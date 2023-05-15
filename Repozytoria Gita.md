up: [[090 Git MOC]]
#status/in-progress 
#tech-area/git 


**Lokalne:**

`git init` - tworzy lokalne repozytorium poprzez utworzenie folderu `.git`, który zawiera [[wszystko co potrzebne do funkcjonowania repo gita]]
`git clone <url> [directory_name]` - tworzy lokalne repozytorium bazując na folderze `.git` z repo klonowanego z internetu; klonowanie ściąga praktycznie wszystko z serwera, każdą wersję pliku, wszystkie branche, historię, etc.


**Zdalne:**

`git remote add <short_name> <URL>` - dodanie remote'a do projektu
`git remote` - wypisuje skrócone nazwy remote'ów połączonych z naszm lokalnym repo
`git remote -v` - skrócone nazwy z URLami
`git remote show <remote>` - pokazanie, które branche z repo zostają uploadowane na które branche repo remote
`git remote rename <old_remote_name> <new_remote_name>` - zmiana nazwy remote repo I WSZYSTKICH BRANCHY, KTÓRE NA NIM SIEDZĄ
`git remote remove <remote>` - usunięcie remote repo z projektu razem ze wszystkimi jego branchami i ustawieniami


`git fetch <remote>` - ściągnięcie wszystkich zmian z remote'a na lokalne repo
`git pull` - ściągnięcie wszystkich zmian na remote branchu i zmergowanie ich do aktualnie aktywnego branchu na lokalnym repo
`git push <remote> <branch>` - upload zmian na remote'a; jeśli lokalne repo nie jest up-to-date z remotem (bo ktoś inny już coś spushował), push zostanie odrzucony

Jest ustawienie konfiguracji `pull.rebase ["true"/"false]"` - domyślne zachowanie rebasowania podczas pullu.



