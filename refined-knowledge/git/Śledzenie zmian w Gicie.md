up: [[080 Git MOC]]

**Git nie zapisuje zmian między plikami, ale zapisuje pliki w ich różnych stanach jako tzw. _snapshots_. Każdy nowy commit powoduje wygenerowanie nowego _snapshota_.**

**Jeżeli pliku nie ma w żadnym _snapshocie_, jest on nieśledzony.** Wówczas można:
- dodać go do _snapshota_; Git zaczyna go śledzić i wypisywać w statusie
- wywołać `git rm --cached <path>`; Git przestaje go śledzić **ale nadal wypisuje go w statusie**
- dodać go do [[Plik .gitignore|pliku .gitignore]]; **Git przestaje wypisywać go w statusie**

Dla plików śledzonych Git definiuje trzy sekcje:
- przestrzeń robocza *(ang. working directory/workspace)* - aktualny stan projektu dla konkretnego _snapshota_ plus dokonane na nim zmiany (które nie są jeszcze nigdzie zapisane)
- obszar przygotowany *(ang. staging area/index)* - zmiany wyselekcjonowane do _zacommitowania_
- [[Repozytoria Gita|repozytorium lokalne]] 

###### Zarządzanie zmianami

```bash
git restore <path> # cofnięcie zmian z workspace; pliki wrócą do stanu ze snapshota
git add <path> # dodanie zmiany pliku lub nowego pliku z workspace do indexu
git rm <path> # dodanie usunięcia pliku z workspace do indexu
git restore --staged <path> # cofnięcie zmian z indexu do workspace'a
git commit -m "message" # zacommitowanie do repo zmian z indexu; wiadomość jest konieczna!
git commit -a # zacommitowanie do repo zmian z workspace (tylko zmodyfikowanych plików, nie nowych!)
```

###### Listowanie zmian

Stan każdego z plików można podejrzeć poprzez `git status` - zostaną pokazane pliki nowe (nieignorowane), zmodyfikowane oraz przygotowane do commitu.
Można też `git status -s`, wtedy wypisany jest trochę krótszy.

```bash
git diff # wszystkie unstaged zmiany wewnątrz plików
git diff --staged # wszystkie staged zmiany wewnątrz plików
git diff --check # wszystkie niepotrzebne spacje
git diff <branch1>...<branch2> # zmiany istniejące na "branch2", których nie ma na "branch1"; bazując na commicie wspólnym dla obu
```


