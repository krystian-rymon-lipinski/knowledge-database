up: [[090 Git MOC]]
#status/in-progress 
#tech-area/git 

**Gałęzie, to nic innego jak wskaźniki na konkretne commity w repozytorium.** Utworzenie nowej gałęzi, to tak naprawdę utworzenie nowego wskaźnika.

**Aby określić, na której gałęzi aktualnie jesteś, Git używa specjalnego wskaźnika HEAD.** Aby zobaczyć, na którą gałąź wskazuje aktualnie HEAD, wystarczy zawołać: `git log --decorate`. Po zrobieniu commita, zostanie on "dopisany" do tej gałęzi, na którą wskazywał HEAD w momencie commita. (Czyli nowy commit będzie wskazywał wstecz na commit, na który wskazywała aktualna gałąź.)

**Git trzyma gałęzie jako pliki, które zawierają checksumę wskazującą na konkretny commit.** Zawierają więc ledwie 40 bajtów (bo tyle waży checksuma) plus 1 dodatkowy przewidziany na nową linię.

Przełączanie między gałęziami najlepiej robić, kiedy wworking directory jest bez żadnych zmian, inaczej może to być niemożliwe z powodu konfliktów między dwiema wersjami. Można sobie z tym poprzez [[Stashowanie gita|stashowanie zmian]] i czyszczenie working directory.

`git branch` - wylistowanie wszystkich gałęzi w repo (aktualna jest oznaczona \*)
`git branch --all` - wylistowanie wszystkich gałęzi w repo lokalnym i zdalnym
`git branch -v` - wylistowanie ostatnich commitów na wszystkich gałęziach
`git branch --merged/--no-merged` - wylistowanie tylko tych gałęzi, które są/nie są zmergowane do aktualnie aktywnej; usunięcie niezmergowanych poprzez `-d` spotka się z błędem (trzeba użyć `-D`, by usunąć takiego brancha, spowoduje to usunięcie pracy niezapisanej nigdzie indziej, a więc jej utracenie)
`git branch --merged/--no-merged <branch_name>` - wylistowanie nie/zmergowanych gałęzi w stosunku do gałęzi "branch_name"
`git branch <branch_name>` - utworzenie nowej gałęzi
`git branch -d <branch_name>` - usunięcie gałęzi "branch_name"
`git branch --move <old_name> <new_name>` - zmiana nazwy brancha
`git push --set-upstream <remote> <new_name>` - utworzenie na remote repo nowego brancha z nową nazwą i powiązanie jej z branchem ze zmienioną nazwą na lokalnym repo; **stary branch wciąż będzie istniał w repo!** (ale będzie można go usunąć, bo wszystkie commity będą na nowym, a i nowe będą leciały już na nowy branch)
`git push <remote> --delete <name>` - usunięcie brancha z remote repo

**Można zmienić nazwę brancha głównego (master/main/develop/whatever) w dokładnie taki sam sposób, ale należy się upewnić, że stara nazwa nie jest nigdzie indziej wykorzystywana.** Np. w skryptach CI/CD, dokumentacjach, konfiguracjach, ustawieniach repo, pull requestach, etc.

`git switch <branch_name>` - przełączenie się na istniejącą gałąź (czyli po prostu przestawienie wskaźnika HEAD, żeby wskazywał na inną gałąź); powoduje również odświeżenie stanu plików z working directory, bo nasz wskaźnik gałęzi wskazuje na inny stan
`git switch -c <branch_name>` - utworzenie nowej gałęzi i przełączenie się na nią
`git switch -` - powrót do poprzednio aktywnej gałęzi
`git merge <branch_name>` - dołączenie gałęzi "branch_name" do aktualnie aktywnej gałęzi (tej, na którą wskazuje wskaźnik HEAD)

---
[[Branche związane z remotem]]
[[Branching workflow]]
[[Typy mergowania]]





