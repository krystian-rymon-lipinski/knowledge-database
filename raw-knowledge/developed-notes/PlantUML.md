up: [[pluginy Android Studio]]
#tech-area/design
#status/3-freezer

**Narzędzie do tworzenia plików UML poprzez opisywanie w tekście obiektów i ich relacji między nimi.**

Przykład dla diagramu klas:

```PlantUML
@startuml  
'https://plantuml.com/class-diagram  
  
abstract class AbstractList  
abstract AbstractCollection  
interface List  
interface Collection  
  
List <|-- AbstractList  
Collection <|-- AbstractCollection  
  
Collection <|- List  
AbstractCollection <|- AbstractList  
AbstractList <|-- ArrayList  
  
class ArrayList {  
Object[] elementData  
size()  
}  
  
enum TimeUnit {  
DAYS  
HOURS  
MINUTES  
}  
  
@enduml
```

---
https://plantuml.com/class-diagram