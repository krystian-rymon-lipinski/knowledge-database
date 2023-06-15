up: [[013.1 Junit MOC]]

**Dodatkowe oznaczenia w kodzie JUnit.**

###### Logika zestawu testów
- **@BeforeClass** - oznaczenie metody jako wykonywanej **raz** przed wszystkimi testami; metodę trzeba oznaczyć jako statyczną!
- **@AfterClass** - oznaczenie metody jako wykonywanej  **raz** po wszystkich testach; metodę trzeba oznaczyć jako statyczną!
- **@Before** - oznaczenie metody jako wykonywanej przed każdym testem
- **@After** - oznaczenie metody jako wykonywanej po każdym teście

###### Pojedynczy test
- **@Test** - oznaczenie metody jako przypadku testowego; można zdefiniować dodatkowe oczekiwania:
	- *@Test(timeout=500)* - test nie przejdzie, jeśli będzie trwał dłużej niż zdefiniowana liczba w milisekundach
	- *@Test(expected=Exception.class)* - test przejdzie tylko, jeśli zostanie wyrzucony spodziewany błąd
- **@Ignores** - zignorowanie przypadku testowego, nie będzie on wykonywany