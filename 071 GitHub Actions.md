up: [[070 CI-CD MOC]]
#status/2-backlog
#tech-area/ci-cd

**Jedna z platform do implementowania automatycznej integracji i dostarczania (a bit mouthful).**

Pozwala wykonywać *workflowy* w reakcji na konkretne wydarzenie w repozytorium (utworzenie issue, pushowanie commita, utworzenie pull requesta, etc.). Można też odpalać je manualnie w dowolnym momencie lub ustawiać na konkretny czas.
Te workflowy składają się z jobów,  joby z *kroków*, które mogą być zdefiniowane jako *akcje* lub skrypty. Akcje to rozszerzenia zdefiniowane przez Githuba. Każdy job wykonuje się na swoim runnerze wirtualnej maszyny - sekwencyjnie lub współbieżnie.

Workflowy pisane są w [[YAML|YAML-u]]





---
Narzędzie do stawiania CI/CD dla kodu, który jest wrzucany na githuba.

https://docs.github.com/en/actions/learn-github-actions/environment-variables#default-environment-variables - environmental variables
GITHUB_WORKSPACE - The default working directory on the runner for steps, and the default location of your repository when using the [`checkout`](https://github.com/actions/checkout) action. For example, `/home/runner/work/my-repo-name/my-repo-name`.

Uwaga, zdublowany folder z repo

Domyślna ścieżka względna (./) jest folderem głównym repo, w którym zawiera się wszystko - tym drugim, tym schowanym głębiej.

Jeśli chce się skorzystać z plików wewnątrz, trzeba przejść sobie po strukturze albo skorzystać z argumentu: 
*working-directory


---
https://docs.github.com/en/actions