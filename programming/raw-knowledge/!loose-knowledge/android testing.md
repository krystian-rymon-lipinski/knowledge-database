Testing in Android

app/src/androidTest -> for tests in UI (clicking buttons, checking fields, etc.); requires real or virtual device and testing framework (Espresso, UI automator) [instrumented tests]

app/src/test -> for tests that do not require Android, e.g. unit tests OR integration tests checking connection with server or smth

Now:

testImplementation: adds dependency for test source set
androidTestImplementation: adds dependency for androidTest source set 

Android Test Runners

@RunWith is needed only when mixing JUnit3 and JUnit4 to distinguish which version should go (probably 4 if you have such a mix...)

https://www.artima.com/weblogs/viewpost.jsp?thread=126923

#tech-area/android 
#tech-area/testing

