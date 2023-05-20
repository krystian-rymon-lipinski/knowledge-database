up: [[090 Git MOC]]
X: [[Łączenie gałęzi Gita]]

**Zamiast łączyć dwie gałęzie rekursywnie, dla jednej z nich można zmienić _commit_, z którego wyrasta.** Skutek będzie ten sam (_snapshot_ będzie posiadał ten sam stan plików), ale historia projektu stanie się bardziej linearna i przejrzysta, bowiem wystarczy później dokonać łączenia gałęzi typu _fast-forward_ bez obaw o ewentualne konflikty (trzeba je rozwiązać już przy zmieniania _commita_).

Operacja jest następująca: 
- Git cofa się do _commita_, który jest przodkiem obu branchy
- ściąga _commity_ (a właściwie bardziej różnice w plikach) z aktualnej gałęzi (tej, która ma być rebazowana) aż do znalezionego wspólnego _commita_ i zachowuje je w tymczasowych plikach
- resetuje aktualną gałąź na ten sam _commit_, na którym jest gałąź, na którą chcemy rebazować
- z zachowanych plików generowane są _commity_ rebazowanej gałęzi wyrastającej już z nowego miejsca

**Nie powinno się rebazować gałęzi wrzuconych na repo zdalne, z których ktoś może korzystać!** Komenda `rebase` usuwa commity i tworzy nowe, więc może to rodzić problem, jeśli ktoś bazuje na pewnych _commitach_, a one zostają usunięte.

**Najlepiej rebazować tylko gałęzie w lokalnym repozytorium.**

```bash
git rebase --onto <target_branch> <current_branch> # rebazowanie gałęzi "current_branch" na gałąź "target_branch"
git rebase --onto <target_branch> <start_commit> <end_commit> # rebazowanie wybranego zakresu commitów na gałąź "target_branch"
git rebase --abort # cofnięcie zmian z rebazowania, gdy jest ono w stanie konfliktu
```
