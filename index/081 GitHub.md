up: [[000 HOME]]
#status/3-freezer 
#tech-area/github

**Jeden z najczęściej wykorzystywanych [[Hostingi Gita|hostingów Gita]].** Oprócz tworzenia repozytoriów kodu  pozwala na trzymanie issues, tworzenie projektów, etc.

CODESPACES! Co to, po co to?

- generowanie kluczy SSH i GPG

Po utworzeniu forka można pull requestować do oryginalnego repo.

Można linkować issuesy i PR-y w innych issuesach i PR-ach poprzez # \<number>. Również z innych repo i projektów. Aczkolwiek można wrzucić po prostu URL-a i GitHub skróci do tylko wymaganych informacji.

Można pisać w [[Markdown|markdownie]] praktycznie w każdym okienku, które widać.

Istnieją konta Organizacji (firm).

Można integrować githuba z innymi serwisami w internecie, np. mailem. Wystarczy podać URL-a i określić, które eventy powinny go triggerować, wraz z ewentualnym payloadem (danymi), który będzie przetwarzany po stronie otrzymującej wiadomość. https://docs.github.com/en/webhooks-and-events/webhooks/about-webhooks

GitHub ma swoje API! 


Specjalne pliki, które GitHub interpretuje:
- README (najczęściej .md) - będzie pokazany w widoku repozytorium; można tu udostępnić wszelkie informacje o projekcie: po co jest, jak go skonfigurować, przykłady, licencje, etc.; można dodawać linki, tabele, obrazki, etc.
- CONTRIBUTING (z dowolnym rozszerzeniem) - przy tworzeniu PR-a, pojawi się info z linkiem do tego pliku; można tam zamieścić informacje, jak tworzyć PR-y, branche, "how to contribute"


Można wciąż używać GitHuba z command line'a: https://cli.github.com/