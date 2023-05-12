up: [[Dependencje Gradle]]

**Definicje oznaczające, do czego jest potrzebny kod z danej dependencji.** Najczęściej definiowane dependencje:

- `implementation` - potrzebna do skompilowania kodu i jego wykonania
- `testImplementation` - potrzebna do skompilowania i wykonania [[014 Android Testing|testów lokalnych]]
- `compileOnly` - potrzebna tylko do skompilowania kodu
- `runtimeOnly` - potrzebna tylko do wykonania kodu
- `androidTestImplementation` - potrzebna do [[014 Android Testing|testów instrumentacyjnych]] na Androida; udostępniana przez androidowy plugin Gradle

- `annotationProcessor` - potrzebna do przeprocesowania [[Annotacje|annotacji]] w bibliotekach opartych na Javie; jeśli jakaś zewnętrzna biblioteka używa swoich własnych annotacji, powinna dostarczyć również narzędzie do ich przeprocesowania, które można włączyć jako dependencję do projektu; 
- `kapt` - Kotlin Annotation Processing Tool -  annotation processor dla bibliotek opartych na Kotlinie (zintegrowanych z jego kompilatorem)

Możliwe jest również zainkorporowanie kodu z innego modułu poprzez: `implementation(project(":<module_name>"))`
