up: [[080 Git MOC]]

**Zmiany dokonane w repozytorium można listować poprzez `git log`, który listuje WSZYSTKIE commity dla aktualnie aktywnego brancha - ich _checksumy_, autorów i daty. Można dopisać dodatkowe parametry, by wyfiltrować tylko wybrane.

```bash
-<number> # tylko n ostatnich commitów
-p # pokazuje dokładne różnice w plikach (z diffem)
--stat # pokazuje listę plików, które zostały zmienione w commitach
--graph # pokazuje zależności między commitami
--no-merges # tylko commity niebędące mergami
--since<date> # tylko commity od określonej daty w formacie YYYY-MM-DD
--until<date> # tylko commity do określonej daty w tym samym formacie
-- <path> # pokazuje tylko commity, które zmieniły coś w podanej lokalizacji (musi to być ostatni parametr komendy)
```

Można również filtrować po elementach _commita_, używając frazy lub [[Wyrażenia regularne|wyrażenia regularnego]]. 

```bash
--author="phrase" # filtrowanie po autorze
--grep="<regex_pattern>" # filtrowanie po wiadomości commita
```

Wiadomości logów można [[Formatowanie logów Gita|formatować]].
