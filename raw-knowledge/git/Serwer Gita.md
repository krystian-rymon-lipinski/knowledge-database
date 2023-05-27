up: [[090 Git MOC]]
#status/3-freezer 
#tech-area/git 

Miejsce, z którego deweloprzy ciągną dane i wrzucają swoje zmiany. Na dobrą sprawę nie potrzebuje working directory, żadne zmiany nie będą tutaj zachodziły. Musi tylko trzymać folder .git, więc jest to tzw. *gołe repozytorium*. Zamiast tworzenia swojego serwera, można wykorzystać [[Hostingi Gita|hostingi]].


Potrzebuje protokołów, żeby transferować dane. Możliwe protokoło to: lokalny, HTTP, SSH, Git.

Tworzenie gołego repozytorium:
`git clone --bare <folder> <nazwa_gołego_repo>`
Później można je wrzucić na serwer poprzez `scp`.

Dla protokołu SSH trzeba wygenerować klucz SSH, żeby móc czytać z i pisać do repo. No i serwer musi jakoś zarządzać tymi kluczami.


Można dołożyć na serwerze bazowy user interfejs - GitWeb.
Nieco bardziej zaawansowanym interfejsem jest GitLab. Daje on duże możliwości łatwego zarządzania użytkownikami, nadawania im praw, tworzenia repozytoriów, etc.


