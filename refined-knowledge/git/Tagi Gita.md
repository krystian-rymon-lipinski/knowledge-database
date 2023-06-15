up: [[080 Git MOC]]

**Umożliwiają oznaczanie istotnych _commitów_, np. _releasowych_.** Istnieją dwa typy tagów:
- lekkie _(ang. lightweight)_ - wskaźnik na konkretny commit i nic więcej, nie posiada nawet wiadomości
- z adnotacją _(ang. annotated)_ - obiekt w bazie danych gita; mają swoją checksumę, tagującego i wiadomość; musi posiadać wiadomość, jak commit; tagujący _commita_ nie musi być tą samą osobą, która _commitowała_ konkretne zmiany.

**Można się przełączyć na konkretnego taga (_commita_ oznaczonego tagiem).** Wiąże się to jednak z przejściem repo w stan "_detached HEAD_". Oznacza to, że można dokonywać zmian i _commitować_ je, ale żaden z tych _commitów_ nie będzie częścią brancha i będzie można się do nich dostać tylko przez ich checksumy. Same te commity będą oddzielone _(ang. detached)_ od całego projektu.

```bash
git tag <tag_name> # utworzenie lekkiego taga dla aktualnego commita
git tag -a <name> -m <message> # utworzenie taga z adnotacją dla aktualnego commita
git tag <tag_name> <commit_hash> #utworzenie lekkiego taga dla wyznaczonego commita
git show <tag_name> # zczytanie commita dla taga lekkiego lub dodatkowych informacji o tagu z adnotacją
git tag -l ["glob_pattern"] # wylistowanie wszystkich tagów [przefiltrowanych przez wzorzec]
git tag -d <tag_name> # usunięcie taga z lokalnego repo
git describe <branch_name> # utworzenie nazwy commita w formie: ostatni tag z adnotacją, liczba commitów od niego, checksuma wybranego
git describe --tags <branch_name> # utworzenie nazwy commita uwzględniając również lekkie tagi
```

```bash
git push <remote> <tag_name> # wypchnięcie taga do zdalnego repo
git push <remote> --tags # wypchnięcie wszystkich tagów do zdalnego repo
git push <remote> --follow-tags # wypchnięcie wszystkich tagów z adnotacją do zdalnego repo
git push origin --delete <tag_name> # usunięcie taga ze zdalnego repo

```









