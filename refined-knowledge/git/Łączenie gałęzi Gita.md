up: [[Gałęzie Gita]]
X: [[Rebazowanie gałęzi Gita]]

**Dołączanie _commitów_ jednej gałęzi do innej _(ang. merging)_.** Może się nie powieść z uwagi na konflikty, które wystąpią, gdy na obu gałęziach nastąpiły zmiany w tych samych miejscach.

```bash
git merge <branch_name> # dołączenie gałęzi "branch_name" do aktualnie aktywnej gałęzi
git merge --squash <branch name> # dołączenie commitów z gałęzi "branch_name" do aktualnej nie jako merge ale jako jeden commit ze wszystkimi zmianami
git cherry-pick <commit_sum> # dołączenie pojedynczego commita do aktualnego brancha; cherry-pick nie jest kopią, ale zupełnie nowym commitem z tymi samymi zmianami
git merge --abort # cofnięcie zmian z merga, gdy ten w stanie konfliktu
git cherry-pick --abort # cofnięcie zmian z cherry-picka, gdy ten jest w stanie konfliktu
```

Typy _mergowania_:

- _fast-forward_ - gdy _commity_ z gałęzi dołączanej pochodzą w prostej linii od _commitów_ z gałęzi docelowej; Git przesunie po prostu wskaźnik gałęzi docelowej na ostatni nowo dołączony _commit_
- _recursive_ - gdy takiej prostej linii nie ma; Git znajduje wówczas _commit_ wspólny dla obu gałęzi i najpierw dołącza zmiany z aktualnie aktywnej gałęzi, a następnie zmiany tej, która jest dołączana; powstaje wówczas _commit_, który ma dwóch rodziców, wkazujący na obie gałęzie, które się na niego złożyły

Powstanie konfliktów możliwe jest tylko przy tym drugim typie. Wówczas w plikach, w których występują, są pokazywane przez znaczniki:

<<<<<<<<<<<< - początek zmian z gałęzi, na który wskazuje HEAD (aktualnie aktywnej)
jakieś zmiany w pliku tutaj
=============== - przedzielenie dwóch wersji
jakieś inne zmiany tutaj
\>>>>>>>>>>>>>>>> - koniec zmian z gałęzi ołączanej