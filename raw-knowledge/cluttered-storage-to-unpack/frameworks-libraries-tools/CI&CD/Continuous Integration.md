up: [[080 CI-CD MOC]]
X: [[Continuous Delivery]]
#status/2-backlog 
#tech-area/ci-cd 

### Continuous Integration
Automatyzacja pewnych czynności, aby wykonywały się w reakcji na określone zdarzenie (**trigger**). Wykonywana po to, aby deweloperzy nie musieli za każdym razem sprawdzać, czy czegoś nie popsuli.

**Dzieje się to na serwerze!** Lokalnie oczywiście można sobie kod zbudować i puścić testy, ale po co? Po to jest właśnie automatyzacja, żeby po pushu sprawdzało się to automatycznie, a deweloper może pisać dalej.

Najczęstszym ustawieniem jest zbudowanie kodu w reakcji na dodanie nowego commitu (lub pull requesta) na głównego brancha.
Na Androidzie dodatkowo można zadać przechodzenie testów jednostkowych i instrumentacyjnych (i pewnie też integracyjnych, jeśli takie istnieją) oraz generowanie plików .apk i .aar.

Tę automatyzację można "wyklikać" w środowiskach lub napisać skrypt.
Skrypty CI tworzy się w:
- bashu (zwykły język skryptowy, rozszerzenie .sh)
- YAML (rozszerzenie .yml)


Generalnie niestety każde środowisko ma inny syntax do tworzenia automatyzacji (**pipeline'a**).
- Jenkins (można pisać w bashu, a można też stworzyć plik Jenkinsfile)
- Azure (YAML)
- GitHub Actions (YAML)


Jeżeli chodzi o taski Androidowe, to wystarczy wywołać komendy [[070 Gradle MOC]]