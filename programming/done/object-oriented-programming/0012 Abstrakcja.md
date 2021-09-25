### Abstrakcja
**Dokładna implementacja zachowania obiektu nie jest istotna. Istotne jest to, co obiekt _udostępnia_.**  Końcowy użytkownik nie musi troszczyć się o szczegóły wykonania konkretnego zadania. Interesuje go jedynie, jakie parametry obiektowi dostarczyć i co zwróci.

Obiekt może za kulisami zmieniać swój stan, wykonywać pracę i komunikować się się z innymi obiektami bez ujawniania, w jaki sposób ani po co to robi.

Zdefiniowanie zachowań dla wielu powiązanych ze sobą obiektów pozwala dostarczyć moduł zajmujący się konkretnym zadaniem (np. analizą obrazów), z którego końcowy użytkownik może wybierać interesujące go operacje, bez żadnej wiedzy o wewnętrznej implementacji. 
W taki sposób tworzy się [[Biblioteka programistyczna|biblioteki programistyczne]], których możliwości opisuje ich [[API|API]].

---

#tech-area/theory/programming-paradigms/object-oriented 
[[0011 Programowanie obiektowe (klasowe)]]


