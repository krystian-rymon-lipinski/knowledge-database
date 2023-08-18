up: [[Azure pipelines]]
#ci-cd-pipeline

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
