up: [[Zmienne (MOC)]]

###### Stosowanie
Domyślnie obiekty są inicjalizowane jako non-null. Utworzenie obiektu typu nullable należy jawnie zadeklarować!
```kotlin
var o1 = SomeObject() 
o1 = null /* ERROR - nie można przypisać wartości 'null' do obiektu non-nullable */
val o2: SomeObject? = SomeObject()
```

Referencja _o1_ przyjmuje jako wartości obiekty typu _SomeObject_. Tylko.
Referencja _o2_ przyjmuje jako wartości obiekty typu _SomeObject_. I null.

```kotlin
val arr1<String?> = arrayOf("Word1", "Word2") /* Jawnie podany typ nullable */
val anotherArray = arrayOf("Word", null) /* Kompilator domyśla się typu z podanych wartości */
```

W Javie na oznaczenie tych typów stosuje się [[Annotacje|annotacje]] @NonNull i @Nullable.