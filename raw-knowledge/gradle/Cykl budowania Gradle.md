up: [[070 Gradle MOC]]
#status/backlog 
#tech-area/gradle 

[[Pliki .gradle]]
**Każdorazowe zbudowanie projektu składa się z 3 faz.**

###### Inicjalizacja
- znalezienie pliku `settings.gradle` (w aktualnej lokalizacji lub w folderach wyżej); sprawdzenie, czy jest to częścią [[Wieloprojektowy build |wieloprojektowego buildu]].
- przechodzi go w celu znalezienia wszystkich modułów wchodzących w skład projektu
- tworzy obiekt `Project` dla każdego modułu 

###### Konfiguracja
- znajduje pliki `build.gradle` dla każdego projektu wchodzącego w skład cyklu
- tworzy [[Graf zadań Gradle|graf zadań]] dla zdefiniowanych i potrzebnych w budowaniu tasków
Można subskrybować notyfikacje na skończoną konfigurację, zbudowanie grafu, dodanie zadania, wykonanie zadania, etc.

###### Egzekucja
- wykonuje wybrane zadania bazując na ich zależnościach opisanych grafem
- wykonanie pliku `build.gradle` powoduje skompilowanie go do obiektu [KotlinBuildScript](https://gradle.github.io/kotlin-dsl-docs/api/org.gradle.kotlin.dsl/-kotlin-build-script/index.html)

---
https://docs.gradle.org/current/userguide/build_lifecycle.html