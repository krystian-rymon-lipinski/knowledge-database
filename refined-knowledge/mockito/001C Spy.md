up: [[042 Mockito MOC]]

**Obiekt z funkcjonalnościami [[001B Mock|mocka]]. Nie jest to imitacja, a pełnoprawny obiekt, na którym można wywoływać metody i oczekiwać efektu, a przy tym pozwala on na [[001D Stubbing|stubbing]] i [[001E Weryfikacja|weryfikację]].**

```java
/* Utworzenia spy'a poprzez metodę: */
SomeObj obj = Mockito.spy(new SomeObj()); /* Parametrem musi być prawdziwy obiekt! */
/* Utworzenie spy'a poprzez annotację: */
@Spy SomeObj obj;
```

Aby ten drugi sposób zadziałał, należy "włączyć" annotacje Mockito poprzez:
a) wywołanie _MockitoAnnotations.initMocks()_
b) użycie [[Test Runner|test runnera]]