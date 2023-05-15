up: [[090 Git MOC]]
#status/in-progress 
#tech-area/git 

**Można dodać alias do dowolnej komendy gita. Jest to element [[Konfiguracja Gita|konfiguracji]], więc można je dodawać dla różnych zakresów Gita.**


`git config --local alias.<command_alias> <git_command>` - dodanie aliasu dla komendy

Jeśli komenda jest dłuższa (bo ma parametry, etc.), należy ją podać w cudzysłowach ' ':

`git config --local alias.last 'log -1'` - git wtłoczy napis w ' ' w miejsce nazwy aliasu