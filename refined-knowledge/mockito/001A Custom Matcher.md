up: [[0018 Argument Matcher]]

**Możliwe jest zdefiniowanie własnego typu matchera i określenie warunków, kiedy należy uznać podany argument za pasujący.**

###### Przykład

Definicja własnego matchera:
```java
public class CustMatcher implements ArgumentMatcher<String> {		
/* Generic klasy jest typem argumentu metody matches(). */
    @Override
    public boolean matches(String arg) {
			arg.contains("phr") 
			/* Warunki na uznanie podanego argumentu za pasujący. */
    }
}
```

Użycie:
```java
when(obj.doSth(argThat(new CustMatcher())).thenReturn("whatever") 
/* Jeśli podany argument spełni warunki CustMatchera, metoda zwróci podany łańcuch. */
obj.doSth(argThat(new CustMatcher())); /* Wywołanie. */
verify(obj).doSth(argThat(new CustMatcher())); 
/* Weryfikacja ze zdefiniowanymi regułami przejścia. */
```