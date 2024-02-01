#tech-area/java
#status/3-freezer

Annotacje. Po coś chyba są.
Wylistować.

Form of metadata, provide data about a program that is not part of the program itself. Annotations have no direct effect on the operation of the code they annotate.

Annotation Processor vs Kapt

---

Java interoperability annotations:

- @JvmOverloads - Instructs the Kotlin compiler to generate overloads for this function that substitute default parameter values.

If a method has N parameters and M of which have default values, M overloads are generated: the first one takes N-1 parameters (all but the last one that takes a default value), the second takes N-2 parameters, and so on.

Parameters must have default values, without this @JvmOverloads is not needed.

- @NonNull i @Nullable - W polach klas czy w konstruktorze? A może tu i tu?
- @Throws - sygnalizacja na potrzeby Javy, że metoda może wyrzucić wyjątek



For example: @Override annotation makes the compiler look for the same method in parent classes and implemented interfaces. It it doesn't find one, compilation error is thrown.

@Deprecated informs, that a particular method is obsolete and should not be used. Compilator will throw a warning otherwise.




Also: https://medium.com/@mmlodawski/https-medium-com-mmlodawski-do-not-always-trust-jvmoverloads-5251f1ad2cfe

**Przydatny przy tworzeniu własnych widoków / custom views!** Trzeba wówczas podać kompilatorowi konstruktor z AttributeSet i defaultStyleAttribute - albo oddelegować to kopmilatorowi poprzez annotację.




@JvmStatic - ?

@JvmField - ?


---

Usually, libraries interact with annotations in one of these two ways:

- **Using reflection.** Library code can query annotations at runtime to perform certain logic. These libraries would normally be packaged as a single artifact and would not require using `kapt` or `annotationProcessor`. Example: Retrofit, which accesses annotations using reflection and doesn't include an annotation processor.
- **Using an annotation processor.** Annotation processors are compiler plugins that get invoked before the main compilation step, can access annotations and the code around them, and perform tasks based on this input. Annotation processors usually come in separate artifacts since they contain code that is not needed at runtime, hence it shouldn't be packaged into your APK. Example: Butterknife, which processes annotations during compilation and comes with a separate `butterknife-compiler` module that contains the annotation processor. You should use `butterknife-compiler` as a `kapt` or `annotationProcessor` dependency, and not `implementation`, `api` or `compile`, since you don't need the annotation processor during runtime.

---

JSR-330 **standardizes annotations like @Inject and the Provider interfaces for Java platforms**. It doesn't currently specify how applications are configured, so it has no analog to Guice's modules. Guice implements a complete JSR-330 injector. This table summarizes the JSR-330 types and their Guice equivalents.