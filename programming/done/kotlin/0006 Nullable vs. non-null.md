### Nullable vs. non-null

###### Stosowanie
Domyślnie obiekty są inicjalizowane jako non-null. Utworzenie obiektu typu nullable należy jawnie zadeklarować!
```kotlin
val o1 = SomeObject() 
o = null /* ERROR */
val o2: SomeObject? = SomeObject()
```

Referencja _o1_ przyjmuje jako wartości obiekty typu _SomeObject_. Tylko.
Referencja _o2_ przyjmuje jako wartości obiekty typu _SomeObject_. I null.

```kotlin
val arr1<String?> = arrayOf("Word1", Word2") /* Jawnie podany typ nullable */
val anotherArray = arrayOf("Word", null) /* Kompilator domyśla się typu z podanych wartości */
```

W przypadku _someArray_ jawnie podano typ nullable. 
W przypadku _anotherArray_ kompilator domyśla się typu z podanych wartości. 


W Javie na oznaczenie tych typów stosuje się [[raw-knowledge/!shards/Annotacje|annotacje]] @NonNull i @Nullable.


#tech-area/kotlin 
[[0000 (MOC) Zmienne]]