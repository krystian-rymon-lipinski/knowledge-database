up: [[100 Azure DevOps]]
#status/3-freezer 
#tech-area/ci-cd 

- [dokumentacja](https://learn.microsoft.com/en-us/azure/devops/pipelines/yaml-schema/?view=azure-pipelines) tworzenia skryptów CI w YAML-u
- [przykłady](https://learn.microsoft.com/pl-pl/azure/devops/pipelines/ecosystems/android?view=azure-devops) najczęściej wykorzystywanych operacji 
- definicja [taska Gradle](https://learn.microsoft.com/en-us/azure/devops/pipelines/tasks/reference/gradle-v2?view=azure-pipelines) z jego możliwościami

When a pipeline is in its own directory, the context on which it operates is still the repository's root directory, regardless of the location of the pipeline YAML file.

Azure Pipelines always executes tasks within the context of the repository where the pipeline YAML file resides, irrespective of the directory structure or the location of the pipeline YAML file.

---

YAML PR triggers are supported only in GitHub and Bitbucket Cloud. If you use Azure Repos Git, you can configure a [branch policy for build validation](https://learn.microsoft.com/en-us/azure/devops/repos/git/branch-policies#build-validation) to trigger your build pipeline for validation.

---

Jeżeli chodzi o testy instrumentacyjne, to można je odpalać na fizycznych urządzeniach hostowanych przez Azure w usłudze [AppCenter](https://appcenter.ms/). Jest to jednak niestety płatne.
Alternatywą jest odpalanie ich na [[Emulator Android Studio|emulatorze]], co jest możliwe i jak najbardziej działa.

---

Można definiować template'y, jeżeli istnieją taski (np. task Gradle@2), dla których trzeba za każdym razem definiować tę samą konfigurację z kilkoma zmianami.

---
[[Azure Android Integration Pipeline|Android Integration Pipeline]]
