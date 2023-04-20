up: [[Pluginy Gradle]]
X: [[Pluginy skryptowe Gradle]]

**Pluginy binarne są skompilowane i spakowane jako pliki JAR, zawierające kod pluginu oraz dodatkowe zasoby, których może potrzebować** (jak np. dodatkowe biblioteki lub pliki konfiguracyjne).
**Są definiowane przez swoje id.**

By zastosować core'owe pluginy, wystarczy podać ich krótką nazwę. Dla pozostałych trzeba najpierw zdefiniować [[Repozytoria Gradle|repozytoria]], gdzie ich szukać. Deklarowanie pluginów może się odbyć na dwa sposoby:

- [[Deklarowanie pluginów Gradle przez `plugins` DSL|przez `plugins` DSL]]
- [[Deklarowanie pluginów Gradle przez 'buildscript'|przez 'buildscript']]