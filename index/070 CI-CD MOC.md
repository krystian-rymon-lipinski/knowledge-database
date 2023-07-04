up: [[000 HOME]]

**Continuous Integration/Continuous Delivery** - automatyczne wykonywanie operacji na kodzie źródłowym trzymanym na zdalnym repozytorium w reakcji na określone zdarzenie _(trigger)_

- [[Continuous Integration]]
- [[Continuous Delivery]]

**Różne narzędzia oferują funkcjonalności CI/CD:**
- [[071 GitHub Actions]] (YAML)
- [[100 Azure DevOps]] (YAML)
- [[083 Jenkins]] (Jenkinsfile pisany w Groovy DSL)
- [[084 TeamCity]]
- [[085 Travis CI]]
- [[086 Circle CI]]
- [[087 Bitrise]]

Automatyzację można zaimplementować korzystając z interfejsu narzędzia lub pisząc skrypt w rozmaitych językach: [[YAML]], bash, PowerShell, Groovy, Python, etc.

Konkretne operacje automatyzacji projektu Androidowego można definiować w skrypcie jako [[Zadania Gradle|zadania Gradle]], np. `assembleDebug`, etc.