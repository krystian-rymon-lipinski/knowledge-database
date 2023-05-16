up: [[090 Git MOC]]
#status/in-progress 
#tech-area/git 

###### Rebasing
Dla rozgałęzionej historii można wykorzystać rebasing zamiast merga. Skutek jest ten sam (ten sam stan plików), ale historia jest linearna, co ułatwia jej śledzenie. Łatwiej jest też osobie, która aplikuje zmiany do głównego brancha, bo wystarczy zrobić fast-forward merga i nie trzeba się obawiać o konflikty.

Operacja jest następująca: 
- git cofa się do commita, który jest przodkiem obu branchy
- ściąga commity (a właściwie bardziej różnice w plikach) z aktualnego brancha (tego, który ma być rebase'owany) i zachowuje je w tymczasowych plikach
- resetuje aktualny branch na ten sam commit, na którym jest branch, na którego chcemy się rebase'ować 
- dodaje zmiany z rebase'owanego brancha (te z zachowanych plików)

**Jest to po prostu przeniesienie brancha tak, żeby wyrastał z innego commita.**

**Nie powinno się rebase'ować branchy wrzuconych na repo, z których ktoś może korzystać!** Jako że rebase usuwa commity i tworzy nowe, może to rodzić problem, jeśli ktoś bazował na naszych commitach przy swojej pracy. Rebase usunie te commity, co bardzo utrudni innym pracę.

Rule of thumb: rebaseuj tylko branche lokalnego repo. Na które branche rebase'ować, do już dowolne.
