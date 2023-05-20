up: [[090 Git MOC]]

**Użyteczne modele przy pracy z gitem w większej grupie autorów.**

- repozytorium centralizowane - wszyscy autorzy pchają swoje zmiany do wspólnego repo i biorą stamtąd aktualny stan kodu
- _integration manager_ - istnieje jedno "święte" repo, do którego commituje tylko jedna osoba: _integration manager_ właśnie; autorzy klonują święte repo i pracują na swoich osobnych repo, po czym proszą integratora, żeby wziął ich zmiany poprzez _pull requesta_, nie mają bowiem uprawnień zapisu do świętego repo
- dyktator i sierżanci -flow podobny do _integration managera_; do świętego repo zmiany wprowadza tylko jedna osoba (tutaj dyktator), ale bierze on kod tylko od sierżantów; każdy taki sierżant sprawuje kontrolę nad wycinkiem projektu i przyjmuje zmiany od autorów skupiających się na tym konkretnym elementem

Model _integration managera_/dyktatora jest często spotykany przy projektach _open-source_, ponieważ autor wrzucający na święte repo ma ścisłą kontrolę nad tym, co tam trafia, a jednocześnie każdy z deweloprów pracuje na tej samej kopii kodu. Taki projekt często posiada plik Documentation/SubmittingPatches, opisujący, w jaki sposób proponować swoje poprawki głównemu kontrybutorowi.

Najczęściej dzieje się to przez **pull-requesty** lub **patche** (wysyłane mailem).

```bash
git request-pull <start-commit> <my_repo> <end-commit> #utworzenie pull requesta
git format-patch # generowanie patcha
git am # akceptowanie patcha
```




