up: [[Gałęzie Gita]]
#status/in-progress 
#tech-area/git 

1. Progressive-stability
Istnieje jeden branch (najprawdopodobniej master), na którym kod jest sprawdzony, przetestowany, stabilny i tylko stąd idzie do releasu. Istnieją branche, na którym kod może być mniej stabilny, ale coś może już działać (np. develop), gdzie po dokładnych testach można to mergować do mastera. No i branche tematyczne, gdzie rzeczy dopiero się tworzą i mają prawo być niedopracowane. Po skończeniu takiego tematu idzie on dopiero do develop.
2. Topic branches
Do każdego feature'a, fixa, hotfixa, etc. można (i należy) tworzyć osobnego brancha. Łatwiej później śledzić zmiany podczas review, testowania, mergowania i 