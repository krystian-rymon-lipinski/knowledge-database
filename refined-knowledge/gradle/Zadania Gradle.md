up: [[070 Gradle MOC]]

**Zadania Gradle** (_ang. Gradle tasks_) **to części _buildu_, które wykonują określoną pracę.** Przykładowe zadania to skompilowanie kodu, wygenerowanie dokumentacji lub przejście testów jednostkowych.
[[Najczęstsze zadania Gradle|Niektóre z nich]] są na tyle podstawowe, że posiadają własne konwencje - niezależnie od pluginu, w którym są zdefiniowane, robią dla projektu bardzo podobne rzeczy.

**Wszystkie zadania wywołuje się poprzez komendę `gradle` lub skrypty [[Gradle wrapper|Gradle wrappera]]**, które wołają tę komendę za kulisami. Lepiej jest to robić przez skrypty - oczywiście trzeba najpierw przenawigować do folderu, który je zawiera.

```bash
./gradlew tasks [--all] # wylistowanie wszystkich tasków gradle dla obecnego projektu
./gradlew :<task_name> # wykonanie konkretnego taska
./gradlew :<module_name>:<task:name> # wykonanie taska zdefiniowanego w subprojekcie
./gradlew clean lint # można oddzielić taski spacją i wywołać ich kilka naraz
./gradlew help --task <task_name> # wylistowanie informacji o konkretnym tasku
```

**Można definiować taski domyślne.** Wówczas wystarczy zawołać `./gradlew`, żeby wykonały się **wszystkie** taski oznaczone jako domyślne.

```kotlin
defaultTasks("task name", "another task name")
```


Zadania mogą od siebie zależeć, co strukturyzuje je w [[Graf zadań Gradle|graf zadań]].
Można również dodawać zachowania do istniejących już tasków.

```kotlin
tasks.named("task_name") {
	/* Wykona się podczas konfiguracji grafu */
	doFirst { /* Wykona się podczas egzekucji tasków */ }
	doLast {  }
}
```
