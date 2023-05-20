up: [[Gałęzie Gita]]

**Na repozytorium zdalnym mogą się pojawiać gałęzie nieutworzone lokalnie** (np. wrzucone przez innego autora). Ściągnięcie informacji o wszystkich gałęzich obecnych na repo zdalnym realizuje się przez `git fetch` (lub `git fetch --all` jeśli projekt posiada więcej przypisanych repo zdalnych). 

**Każda gałąź pobrana ze zdalnego repo to tzw. gałąź zdalna _(ang. remote-tracking branch)_.** Są to wskaźniki na _commity_\ trzymane na zdalnym repo, a ich nazwy to `<remote>/<branch_name>`, np. `origin/master`. Nie można ich przesunąć "z palca" na lokalnym repo, są jedynie odzwierciedleniem konkretnego stanu gałęzi na zdalnym repo i mogą zacząć wskazywać na inne _commity_ po _pushu_, _pullu_ lub _fetchu_.

**Gałęzie na lokalnym repo można powiązać z konkretnymi gałęziami na zdalnym repo. Tworzy to parę gałęzi śledząca/śledzona _(ang. tracking/upstream)_.** 

Utworzenie takiej pary ułatwia synchronizowanie ich stanu między lokalnym a zdalnym repo:
- `git push` powoduje wypchnięcie zmian z gałęzi śledzącej (lokalne repo) na gałąź śledzoną (zdalne repo)
- `git pull` powoduje wywołanie `git fetch` i `git merge` na lokalnym branchu, powodując ściągnięcie zmian z gałęzi śledzonej (zdalne repo) i dołączenie ich poprzez _merge_ do gałęzi śledzącej

```bash
# Cheatsheet dla gałęzi związanych ze zdalnym repo

git switch -c <name> <remote_branch_name> # utworzenie lokalnej gałęzi na bazie gałęzi zdalnej; mają one ten sam stan (bo bazują na tym samym snapshocie)
git branch -u <remote_branch> # powiązanie aktualnej gałęzi lokalnej na lokalnym repo z gałęzią zdalną
git branch -vv # status gałęzi śledzących: jakie są ich gałęzie śledzone i czy są do przodu czy do tyłu w stosunku do nich
git remote show <remote> # pokazanie gałęzi lokalnych ich konfiguracji pod push/pull
git push -u <remote> <branch_name> # wypchnięcie na zdalne repo gałęzi śledzonej przez aktualną gałąź lokalną
git push <remote> --delete <name> # usunięcie gałęzi zdalnej ze zdalnego repo
```

