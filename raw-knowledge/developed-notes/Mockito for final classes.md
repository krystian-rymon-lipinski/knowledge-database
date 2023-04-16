up: [[042 Mockito MOC]]
#status/freezer 
#tech-area/mockito 
#android/gradle-dependency 

```groovy
testImplementation "org.mockito:mockito-core:2.25.1"
```

Mockito 2 już daje taką opcję, ale trzeba jeszcze zrobić jedną rzecz:
- utworzyć folder test/resources/mockito-extensions
- utworzyć w nim plik org.mockito.plugins.MockMaker
- zapisać w pliku frazę: `mock-maker-inline`


Mockito core jest lepsze niż mockito-all. (Chyba że istnieje mockito all w wersji 2+, które udostępnia tę opcję również).