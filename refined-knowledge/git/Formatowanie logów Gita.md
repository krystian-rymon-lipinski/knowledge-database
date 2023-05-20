up: [[Historia commitów Gita]]

**Aby formatować logi _commitów_, należy skorzystać z parametru `--pretty="format:" "`**, gdzie między cudzysłowami można wykorzystać następujące wartości:

1.  `%H`: hash _commita_ (pełny)
2.  `%h`: hash _commita_ (skrócony)
3.  `%an`: imię autora
4.  `%ae`: email autora
5.  `%ad`: data autorstwa
6.  `%s`: wiadomośc _commita_
7.  `%d`: gałęzie i tagi wskazujące na commit
8.  `%cn`: imię commitującego
9.  `%ce`: email commitującego
10. `%cd`: data commitowania

Jednym z zapisanych formatów jest `--pretty=oneline`, który jest opisany jako:
`git log --pretty=format:"%H - %s"`