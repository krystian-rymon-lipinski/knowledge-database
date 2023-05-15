up: [[090 Git MOC]]
#status/in-progress 
#tech-area/git 

**Użyteczne struktury przy pracy z gitem w większej grupie autorów.**

- centralized - wszyscy developrzy pushują do wspólnego repo; git nie pozwoli spushować, jeśli ktoś spushował wcześniej, a my operujemy na przestarzałej wersji repo - trzeba najpierw  pobrać zmiany, a dopiero potem można wysyłać swoje
- with merge conflicts - odmianą cetralized repo jest takie, gdzie nie trzeba być zawsze na najnowszej wersji repo, by pushować; wystarczy, że nasze zmiany nie powodują konfliktu na branchu wskutek innych zmian już na niego pchniętych; jeśli więc pracujemy na osobnych branchach, możemny pushować; problemy (i konflikty) mogą zacząć się dopiero przy próbie mergowania do gałęzi "main"/"master" czy innych zbiorczych
- integration manager - istnieje jedno "święte" repo, do którego commituje tylko jedna osoba: integration manager właśnie; developrzy klonują święte repo i pracują na swoich osobnych repo, po czym proszą integratora, żeby wziął ich zmiany; często spotykany model przy projektach open source'owych
- dictator & lieutenants - podobny do integration managera (tutaj dyktatora), ale jest jeszcze poziom pomiędzy; developerzy robią na swoim repo, sierżanci biorą od nich zmiany, a dyktator może brać zmiany tylko od sierżantów i jako jedyny pushuje zmiany do świętego repo, z którego wszyscy developerzy ciągną zmiany