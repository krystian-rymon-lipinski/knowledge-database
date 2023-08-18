up: [[070 CI-CD MOC]]
#status/3-freezer
#tech-area/ci-cd

**Jedna z platform dostarczająca funkcjonalności CI/CD do wykonywania na konkretnym repozytorium kodu trzymanym na GitHubie.**

Aby tworzyć potoki CI/CD, należy z poziomu GitHub Actions UI utworzyć pierwszy z nich. Spowoduje to utworzenie folderu `.github/workflows` i to w nim należy tworzyć wszystkie następne. Skrypty pisane są w [[YAML|YAML-u]] i definiują _workflow_, dla którego trzeba zdefiniować przynajmniej:
- [_trigger_](https://docs.github.com/en/actions/using-workflows/triggering-a-workflow) (_push_, _pull_request_, utworzenie _issue_, upłynięcie ustalonego czasu, etc.)
- _jobs_: wszystko, co ma się wykonać podczas _workflow_; każdy _job_ wykonuje się na osobnym _runnerze_ wirtualnej maszyny (może współbieżnie) i może się składać z kroków definiowanych przez `steps`

_Trigger_ dotyczący wszystkich gałęzi osiąga się przez:
- `branches: '*'` - łapie wszystkie gałęzie nieposiadające _slasha_ (/)
- `branches: '**'` - łapie wszystkie gałęzie; jest to domyślna konfiguracja dla `branches: `

- [[GitHub Actions Android Integration Pipeline|Android Integration Pipeline]]


---
https://docs.github.com/en/actions/learn-github-actions/environment-variables#default-environment-variables - environmental variables
GITHUB_WORKSPACE - The default working directory on the runner for steps, and the default location of your repository when using the [`checkout`](https://github.com/actions/checkout) action. For example, `/home/runner/work/my-repo-name/my-repo-name`.

Uwaga, zdublowany folder z repo

Domyślna ścieżka względna (./) jest folderem głównym repo, w którym zawiera się wszystko - tym drugim, tym schowanym głębiej.

Jeśli chce się skorzystać z plików wewnątrz, trzeba przejść sobie po strukturze albo skorzystać z argumentu: 
*working-directory

---
https://docs.github.com/en/actions
https://github.com/marketplace
https://docs.gradle.org/current/userguide/github-actions.html