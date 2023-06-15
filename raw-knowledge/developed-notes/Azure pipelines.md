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

```yaml   
# gradle-task-template.yml
parameters:  
  - name: gradleTasks  
    type: string  
    default: 'build'  
  
  - name: displayName  
    type: string  
    default: 'Unnamed Gradle task'  
  
  - name: publishJUnitResults  
    type: boolean  
    default: false  
  
  - name: testResultsFiles  
    type: string  
    default: ''  
  
  - name: continueOnError  
    type: boolean  
    default: false  
  
steps:  
  - task: Gradle@2  
    displayName: ${{ parameters.displayName }}  
    continueOnError: ${{ parameters.continueOnError }}  
    inputs:  
      javaHomeOption: 'JDKVersion'  
      jdkVersionOption: '1.17'  
      workingDirectory: ''  
      gradleWrapperFile: 'gradlew'  
      gradleOptions: '-Xmx3072m'  
      publishJUnitResults: ${{ parameters.publishJUnitResults }}  
      testResultsFiles: ${{ parameters.testResultsFiles}}  
      tasks: ${{ parameters.gradleTasks }}

# integration-pipeline.yml
trigger:  
  branches:  
    include:  
      - '*'  # trigger dla każdego commita na dowolnym branchu
  
pool:  
  vmImage: 'macos-latest'  
  
jobs:  
  - job: 'integration_job'  
    displayName: 'Integration'  
    steps:  
      - template: gradle-task-template.yml  
        parameters:  
          gradleTasks: 'assembleDebug'  # zbudowanie projektu
          displayName: 'Assemble'  
      - template: gradle-task-template.yml  
        parameters:  
          gradleTasks: 'testDebugUnitTest'  #testy jednostkowe
          displayName: 'Test'  
          publishJUnitResults: true  
          testResultsFiles: '**/TEST-*.xml'
	  # Zainstalowanie emulatora
	  - bash: |  
    echo "y" | $ANDROID_HOME/tools/bin/sdkmanager --install 'system-images;android-27;google_apis;x86'   
    echo "no" | $ANDROID_HOME/tools/bin/avdmanager create avd -n xamarin_android_emulator -k 'system-images;android-27;google_apis;x86' --force  
  
    $ANDROID_HOME/emulator/emulator -list-avds  
    echo "Starting emulator"  
  
    nohup $ANDROID_HOME/emulator/emulator -avd xamarin_android_emulator -no-snapshot > /dev/null 2>&1 &  
    $ANDROID_HOME/platform-tools/adb wait-for-device shell 'while [[ -z $(getprop sys.boot_completed | tr -d '\r') ]]; do sleep 1; done; input keyevent 82'  
  
    $ANDROID_HOME/platform-tools/adb devices  
    echo "Emulator started"  
	
	- template: gradle-task-template.yml  
	  parameters:  
	    gradleTasks: 'connectedDebugAndroidTest'  # testy instrumentacyjne
	    displayName: 'Instrumented Testing'  
	    continueOnError: true  
	- task: PublishTestResults@2       # opublikowanie testów
	  displayName: 'Instrumented Testing results'  
	  inputs:  
	    failTaskOnFailedTests: true  
	    testResultsFiles: '**/outputs/androidTest-results/**/*.xml'
```
