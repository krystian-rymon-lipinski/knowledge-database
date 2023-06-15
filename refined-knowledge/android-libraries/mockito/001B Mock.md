up: [[013.2 Mockito MOC]]

**Imitacja obiektu. Jego zachowanie można wymuszać oraz sprawdzać podczas testów jednostkowych.**

```java
/* Utworzenia mocka poprzez metodę: */
SomeObject obj = Mockito.mock(SomeObject.class); 
/* Utworzenie mocka poprzez annotację: */
@Mock SomeObject obj;
```

Aby ten drugi sposób zadziałał, należy "włączyć" annotacje Mockito poprzez:
a) wywołanie _MockitoAnnotations.initMocks()_
b) użycie [[Test Runner|test runnera]]

**Mocki tworzy się, by:**
- kontrolować ich stan i zachowanie poprzez [[001D Stubbing|stubbing]] 
- sprawdzać, czy zachowują się w oczekiwany sposób poprzez [[001E Weryfikacja|weryfikację]]

**Nie można tego robić na zwykłych obiektach, zwrócony zostanie _NotAMockException_.**

**Wywołanie metody obiektu na mocku nie będzie miało żadnego efektu. Odnotowany zostanie jedynie fakt, że nastąpiła interakcja z mockiem.** W celu uzyskania obu tych rzeczy, należy skorzystać ze [[001C Spy|szpiegów]].