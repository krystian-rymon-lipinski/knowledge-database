#status/freezer 
#tech-area/android 
#android/modularity 

Można w AS utworzyć bibliotekę androidową, czyli plik o rozszerzeniu .aar.
Wówczas można go dodać do głównego projektu (File -> Project Structure -> Dependencies) poprzez:
- library dependency (tak jak wszystkie różne JUnity i inne rzeczy)
- jar dependency - wówczas dodaje się tylko plik ze ścieżki
- module dependency - dodaje się moduł istniejący już w projekcie


https://developer.android.com/studio/projects/android-library