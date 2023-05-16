up: [[Gałęzie Gita]]
#status/in-progress 
#tech-area/git 


###### Remote-tracking branches 
Referencje na lokalnym repo do branchy na remote repo; nie można ich przesunąć (na inne commity na przykład); git je przesuwa przy fetchach, pushach, pullach, etc.; generalnie ich stan jest odświeżany po komunikacji z serwerem, na którym leży remote repo; ich nazwy to `<remote>/<branch_name>`, np. `origin/master` albo `origin/this_weird_fix`

`git fetch` - update'uje remote-tracking branches na lokalnym repo
`git fetch --all`  - jeśli jest więcej remote'ów, update'uje wszystkie info z nich na lokalne repo

Można sobie utworzyć własną lokalną branch z remote-tracking poprzez:
`git switch -c <name> <remote_branch_name>` - np. `git switch -c myfeat origin/somefeat`
Wówczas bracnh "myfeat" jest tracking branchem dla bracnha "somefeat".

###### Tracking branches
Branche na lokalnym repo, które są powiązane z branchami na remote repo (tracking branch <-> upstream branch). Ułatwia to pullowanie i pushowanie, bo git już wie, na który serwer i na którą gałąź się kierować.

`git branch -u <remote_branch>` - ustawienie upstream brancha dla lokalnego brancha 
`git branch -vv` - status tracking branchy: jakie są ich upstreamy i czy są do przodu czy do tyłu; oczywiście w stosunku do ostatniego fetcha; jeśli coś się zadziało od tego czasu, lokalne repo nic o tym nie wie

`git pull` - jeśli jest to tracking branch, git wywoła `git fetch` i `git merge`, powodując merge upstream brancha do lokalnego 