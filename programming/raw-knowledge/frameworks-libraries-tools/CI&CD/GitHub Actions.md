Narzędzie do stawiania CI/CD dla kodu, który jest wrzucany na githuba.

https://docs.github.com/en/actions/learn-github-actions/environment-variables#default-environment-variables - environmental variables
GITHUB_WORKSPACE - The default working directory on the runner for steps, and the default location of your repository when using the [`checkout`](https://github.com/actions/checkout) action. For example, `/home/runner/work/my-repo-name/my-repo-name`.

Uwaga, zdublowany folder z repo

Domyślna ścieżka względna (./) jest folderem głównym repo, w którym zawiera się wszystko - tym drugim, tym schowanym głębiej.

Jeśli chce się skorzystać z plików wewnątrz, trzeba przejść sobie po strukturze albo skorzystać z argumentu: 
*working-directory*
