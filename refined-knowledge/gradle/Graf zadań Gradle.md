up: [[Cykl budowania Gradle]]

**Struktura opisująca zależności między [[Zadania Gradle|zadaniami]] podczas budowania projektu.** Jest to [skierowany graf acykliczny](https://en.wikipedia.org/wiki/Directed_acyclic_graph). 

**Żadne z zadań nie zostanie wykonane, dopóki nie zostanie zbudowany cały graf podczas konfiguracji!**

Domyślnie Gradle kończy budowanie, jeśli tylko którekolwiek z zadań się nie powiedzie *(sfailuje)*. Można to zmienić za pomocą parametru `--continue` w konsoli lub ustawiając parametr systemowy `org.gradle.continuous-build` na `true`. Wówczas będzie wykonywać się każde zadanie, ale tylko jeśli poprawnie wykonają się wszystkie zadania, od których zależy.

```kotlin
tasks.register("task_name") {
	dependsOn("another_task_name") /* Ustawienie zależności między zadaniami */
}
```

Można zrezygnować z taska należącego do grafu, na przykład jeśli jest zbędną dependencją.

```bash
./gradlew <big_task> --exclude-task <smol_task>
```

Można się odwołać do grafu ze skryptu budującego poprzez:

```kotlin
gradle.taskGraph.whenReady { /* whenReady, czyli kiedy zostanie zbudowany podczas konfiguracji buildu */
    allTasks.forEach {  
        println(it)  
    }  
}
```