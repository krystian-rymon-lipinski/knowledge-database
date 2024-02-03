up: [[020 Kotlin MOC]]
#status/2-backlog

[[Annotacje]]


@NonNull/@Nullable - 

@Throws - signaling for Java purposes, that a method can throw an exception (Java has checked exceptions, Kotlin does not)

@JvmStatic - ?

@JvmField - ?


---

- @JvmOverloads - Instructs the Kotlin compiler to generate overloads for this function that substitute default parameter values.

If a method has N parameters and M of which have default values, M overloads are generated: the first one takes N-1 parameters (all but the last one that takes a default value), the second takes N-2 parameters, and so on.

Parameters must have default values, without this @JvmOverloads is not needed.


**Przydatny przy tworzeniu własnych widoków / custom views!** Trzeba wówczas podać kompilatorowi konstruktor z AttributeSet i defaultStyleAttribute - albo oddelegować to kopmilatorowi poprzez annotację.

Also: https://medium.com/@mmlodawski/https-medium-com-mmlodawski-do-not-always-trust-jvmoverloads-5251f1ad2cfe