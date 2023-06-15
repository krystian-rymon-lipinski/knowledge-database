up: [[080 Git MOC]]

**W ramach [[Konfiguracja Gita|konfiguracji]] można dodać alias do dowolnej komendy Gita.**

```bash
git config --local alias.<command_alias> <git_command> # dodanie aliasu dla komendy
git config --local alias.last 'log -1' # dla dłuższej komendy (z parametrami, etc.) należy wtłoczyć napis w ' '; wówczas "git last" oznacza "git log -1"
```
