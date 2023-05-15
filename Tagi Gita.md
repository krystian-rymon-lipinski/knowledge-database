up: [[090 Git MOC]]
#status/in-progress 
#tech-area/git 

Umożliwiają oznaczanie istotnych commitów, np. releasowych.

`git tag [-l]` - wylistowanie wszystkich tagów
`git tag -l "<glob_pattern>"` - wylistowanie przefiltrowanych przez kryterium tagów

`git show <tag_name>` - dla lightweight pokazuje tylko commita; dla annotated pokazuje dodatkowe informacje

Można otagować konkretny commit później, wystarczy na koniec komendy `git tag` dodać checksumę commita.

`git push <remote> _tag_name>` - spushowanie taga do remote repo
`git push <remote> --tags` - spushowanie wszystkich tagów do remote repo
`git push <remote> --follow-tags` - spushowanie wszystkich annotated tagów do remote repo

`git tag -d <tag_name>` - usunięcie taga z lokalnego repo
`git push origin --delete <tag_name>` - usunięcie taga z remote repo

**Można się przełączyć na konkretnego taga (commita oznaczonego tagiem).** Wieąże się to jednak z tym, że repo będzie wówczas w stanie "detached HEAD". Oznacza to, że można dokonywać zmian i commitować je, ale żaden z tych commitów nie będzie częścią brancha i będzie można się do no nich dostać tylko przez ich hashe. Same te commity będą - no właśnie - detached. Detached od całego projektu.



###### **Lightweight tags** - wskaźnik na konkretny commit i nic więcej; nie posiada nawet wiadomości
`git tag <tag_name>`

###### **Annotated tags** - obiekt w bazie dancyh gita; mają swoją checksumę, tagującego, wiadomość, etc.; musi posiadać wiadomość, jak commit; tagujący commita nie musi być tą samą osobą, która commitowała konkretne zmiany.

`git tag -a <name> -m <message>` - utworzenie annotated taga
`git show <tag_name>` - sczytanie informacji o annotated tagu





