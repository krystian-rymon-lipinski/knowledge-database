up: [[001E Weryfikacja]]

**Metoda umożliwiająca weryfikację kolejności interakcji z mockiem.**
```java
List<String> mockedList = mock(MyList.class); 
..
InOrder inOrder = Mockito.inOrder(mockedList); 
inOrder.verify(mockedList).size(); 
inOrder.verify(mockedList).add("a parameter"); 
inOrder.verify(mockedList).clear();
```