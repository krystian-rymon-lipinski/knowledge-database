up: [[090 Git MOC]]

**Git jako system typu _DVCS_ operuje repozytoriach lokalnych i zdalnych.** 

###### Repozytoria lokalne

Obecne na maszynie developera jako folder, który zawiera w sobie [[Folder .git|folder .git]]. Można go utworzyć na dwa sposoby:

- `git init` - tworzy lokalne repozytorium poprzez utworzenie folderu `.git`
- `git clone <url> [directory_name]` - tworzy lokalne repozytorium poprzez sklonowanie folderu `.git` z repozytorium zdalnego obecnego pod konkretnym adresem URL

Domyślnie po sklonowaniu zdalnego repozytorium posiada ono alias _origin_. Można podać własny poprzez `git clone <url> -o <name>`. 

Można zrobić _snapshota_ repo poprzez:
`git archive <branch_name> [--format=<format>] [--output=<filename>]`
Domyślnym formatem jest "tar" (ale nalepiej go podać i tak).

###### Repozytoria zdalne

Obecne na [[Serwer Gita|serwerze gita]], najczęściej to do niego pchają swoje zmiany deweloperzy i z niego biorą najnowszą wersję kodu.

```bash
git remote add <short_name> <URL> # dodanie zdalnego repo do projektu
git remote rename <old_remote_name> <new_remote_name> # zmiana nazwy (aliasu) zdalnego repo ORAZ WSZYSTKICH JEGO GAŁĘZI!
git remote remove <remote> # usunięcie zdalnego repo z projektu razem ze wszystkimi jego gałęziami i ustawieniami
git remote [-v] # wypisanie aliasów zdalnych repo projektu [oraz ich URL-i]
git fetch <remote> # ściągnięcie stanu gałęzi repo zdalnego do repo lokalnego
```





