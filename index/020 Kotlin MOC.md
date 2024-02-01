up: [[000 HOME]]
#status/0-revision-needed 

**Język programowania opierający się na paradygmatach [[031 Programowanie obiektowe|obiektowym]] i [[032 Programowanie funkcyjne|funkcyjnym]].**
Napisane w nim programy wykonywane są na [[JVM|maszynie wirtualnej Javy]].


> [!NOTE]
> **Deklaracja najwyższego poziomu** to deklaracja, która nie jest definiowana w zasięgu czegokolwiek, ale w dedykowanym dla niej pliku - jak klasa, interfejs czy funkcja globalna.
> **Moduł** to zespół plików Kotlina kompilowanych jako projekt.

###### Podstawy języka

- [[Zmienne (MOC)|(MOC) Zmienne]]
- [[0005 Równość obiektów|Równość obiektów]]
- [[0007 Bezpieczeństwo 'null'|Bezpieczeństwo 'null']]
- [[0009 Wyjątki|Wyjątki]]
- [[000A Kolekcje|Kolekcje]]

[[Typy sparametryzowane]]

###### Paradygmat [[032 Programowanie funkcyjne|funkcyjny]]

- [[000F Funkcje|Funkcje]]
- [[Wyrażenia lambda]]
- [[Funkcje wyższego rzędu]]
- funkcje infix (omitting the dot)
- funkcje inline
- funkcje rozszerzające (extension functions)
- funkcje zagnieżdżone
- funkcje anonimowe
- tail recursion
###### Paradygmat [[031 Programowanie obiektowe|obiektowy]]

Poza podstawowymi konstrukcjami programowania obiektowego Kotlin definiuje ponadto:

- [[0010 Klasy danych|Klasy danych]]
- interfejs funkcjonalny
- klasy zapieczętowane
- klasy enum
- obiekty - singletony (object, companion object, etc.)
- delegacja ("by" keyword), delegated properties
- type aliases


###### Kotlin Android

- [[Korutyna]]
- [[Przepływ]]



---

Praktycznie wszystko w Kotlinie jest wyrażeniem, które może zostać do czegoś przyrównane:
- if-else
- when
- try-catch 
- throw
- ?