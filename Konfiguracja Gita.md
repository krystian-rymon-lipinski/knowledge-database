up: [[090 Git MOC]]
#status/in-progress 
#tech-area/git 

**Konfigurowanie ustawień Gita odbywa się za pomocą komendy `git config` z wybranym parametrem. Pliki zachowujące konfigurację obecne są na trzech poziomach:**

- `<git_directory_path>/etc/gitconfig` - plik sytemowy, gdzie jego ścieżka zależy od zmiennej środowiskowej podanej podczas [[Setup Gita|setupu Gita]]; można wpłynąć na te ustawienia poprzez parametr `--system`
- `<user_path/.gitconfig` - plik trzymający ustawienia dla wszystkich projektów Git; można na nie wpłynąć poprzez parametr `--global`
- `<project_path>/.git/config` - plik trzymający ustawienia dla konkretnego projektu; można na nie wpłynąć poprzez parametr `--local`

Ustawienia można nadpisywać, najniżej w hierarchii są systemowe, najwyżej - lokalne. Domyślnym parametrem jest `--local`.

Najpopularniejszymi ustawieniami są dane użytkownika:

```bash
git config --global user.name = "User Name" # ustawienie konfiguracji globalnej
git config --global user.email = "user_mail@example.com"
...
git config user.name # sprawdzenie konfiguracji
```

**Wszystkie ustawienia (i ich źródło) można podejrzeć poprzez:**

```bash
git config --list --show-origin
```