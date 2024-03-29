up: [[031 Programowanie obiektowe]]

**Umożliwia zdefiniowanie zachowań wspólnych dla różnych klas. Klasa dziedzicząca po innej może oprócz swoich składowych i metod posiadać takie, które pochodzą od klasy, po której dziedziczy.**

Klasa dziedzicząca to klasa __pochodna__.
Klasa, po której się dziedziczy, to klasa __bazowa__.
Każda nowo powstała klasa dziedziczy po [[0024 Klasa podstawowa|klasie podstawowej]].
Klasa oznaczona jako **finalna** blokuje dziedziczenie po niej.

Nie ma żadnego ograniczenia w kwestii ilości poziomów dziedziczenia - każda klasa pochodna może być dla innej klasą bazową. 
W niektórych językach programowania klasa pochodna może dziedziczyć po wielu klasach bazowych jednocześnie.

###### Przesłanianie
Oprócz definiowania swoich własnych elementów, klasa pochodna może __przesłaniać__ składowe i metody klasy bazowej. Aby to zrobić:
- składowe należy określić tą samą nazwą i typem.
- metody należy określić tą samą nazwą, typem zwracanej wartości oraz parametrami.
- element nie może być oznaczony jako finalny

Wówczas klasa pochodna może korzystać zarówno ze swojej implementacji metody, jak i implementacji klasy bazowej. Należy tylko oznaczyć, z której wersji metody ma skorzystać klasa pochodna.