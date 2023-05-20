up: [[090 Git MOC]]

**Gałęzie, to nic innego jak wskaźniki na konkretne _commity_ w repozytorium.** Utworzenie nowej gałęzi, to tak naprawdę utworzenie nowego wskaźnika. Git trzyma gałęzie jako pliki, które zawierają checksumę wskazującą na konkretny commit. Zawierają więc ledwie 40 bajtów (bo tyle waży checksuma) plus 1 dodatkowy przewidziany na nową linię.

**Aby określić aktualnie aktywną gałąź, Git używa specjalnego wskaźnika HEAD.** Aby zobaczyć, na którą gałąź wskazuje aktualnie HEAD, wystarczy zawołać: `git log --decorate`. Po zmianie aktywnej gałęzi wskaźnik HEAD zaczyna wskazywać na inny _commit_, a Git ładuje stan projektu (pliki) zapisany dla tego konkretnego _snapshota_.

Przełączanie między gałęziami najlepiej robić, kiedy *workspace* jest bez żadnych zmian, inaczej może to być niemożliwe z powodu konfliktów między dwiema wersjami. Można sobie z tym poradzić poprzez [[Stashowanie gita|stashowanie zmian]] z _workspace'a_ i/lub wyczyszczenia go.

**Gałęzie powinno się [[Łączenie gałęzi Gita|łączyć]], aby nabudowywać kolejne nowości do projektu. Należy zaadaptować [[Flow gałęzi Gita|flow gałęzi]] w celu efektywnego zarządzania zmianami w projekcie - ich tworzenia, testowania i dopuszczania na produkcję.**

Niektóre gałęzie mogą być [[Gałęzie związane ze zdalnym repozytorium|związane ze zdalnym repozytorium]]. 

```bash
# Cheatcheet dla gałęzi lokalnego repo

git branch [-v] # wylistowanie wszystkich gałęzi w repo lokalnym [z ich ostatnimi commitami] (aktualnie aktywna będzie oznaczona *)
git branch --all # wylistowanie gałęzi w repo lokalnym i zdalnym
git branch <name> # utworzenie nowej gałęzi o nazwie "name"
git branch --move <old_name> <new_name> # zmiana nazwy brancha
git branch -d <name> # usunięcie brancha o nazwie "name"; jeśli branch jest nigdzie niezmergowany, trzeba użyć -D
git branch --merged/--no-merged # wylistowanie nie/zmergowanych gałęzi w stosunku do aktualnie aktywnej
git branch --merged/--no-merged <branch_name> # wylistowanie nie/zmergowanych gałęzi w stosunku do gałęzi "branch_name"
git switch <branch_name> # przełączenie się na istniejącą gałąź
git switch -c <branch_name> # utworzenie nowej gałęzi i przełączenie się na nią
git switch - # powrót do poprzednio aktywnej gałęzi
```

**Można zmienić nazwę brancha głównego (master/main/develop/whatever) w dokładnie taki sam sposób jak każdego innego, ale należy się upewnić, że stara nazwa nie jest nigdzie indziej wykorzystywana.** Np. w skryptach CI/CD, dokumentacjach, konfiguracjach, ustawieniach repo, pull requestach, etc.










