### Mockito ([API](https://javadoc.io/doc/org.mockito)) (mockito-core)
**[[Framework programistyczny|Framework]] do [[Testy jednostkowe|testów jednostkowych]] oprogramowania  napisanego w Javie. ** Opiera się na koncepcie ***mocków*** - imitatorów zastępujący prawdziwe obiekty, których stan i zachowanie można dowolnie kontrolować poprzez ***stubbing***.

Dzięki temu nie trzeba koncentrować się na inicjowaniu wszystkich składowych testowanego obiektu. Ma to znaczenie szczególnie wtedy, gdy te składowe mają swoje składowe, itd., co wymagałoby tworzenia dziesiątek obiektów, by móc przetestować jeden. W to miejsce można te składowe ***zmockować***.

**Kolejność czynności podczas testowania z użyciem Mockito:**
stubbing -> wywołanie metody na obiekcie -> weryfikacja

###### Elementy frameworka
- [[001B Mock]]
- [[001C Spy]]
- [[001D Stubbing]]
- [[001E Weryfikacja]]
___

#tech-area/testing/unit-testing/mockito 