#status/4-liquid-nitrogen

Obiekty, których stan nie może ulec zmianie po ich utworzeniu. Np. wszystkie ich pola sa oznaczone jako finalne i prywatne i nie ma żadnego settera, dzięki któremu można by je zmienić.

W javie immutable sa wszystkie wrappery do prymitywnych typów i String.

Jeśli będzie się chciało zmienić istniejacy obiekt niemutowalny, zostanie utworzony nowy. Np. przy konkatenacji Stringa, utworzony zostanie nowy obiekt, ale stary zostanie zachowany. Nawet jeśli do któregoś z tych obiektów nie będzie referencji, obiekt będzie istniał. Na wieczność. Bez możliwości odwołania do niego. Bez celu i bez nadziei na niego. Aż do zakończenia pracy programu, który uwolni go wraz z innymi zasobami z tego piekła. Przynajmniej do kolejnego uruchomienia...

String pool. Utworzenie Stringa poprzez String s1 = "Coś" i drugiego tego samego nie tworzy nowego obiektu - dodaje tylko referencje do już istniejacego. Dopiero utworzenie Stringa przez new tworzy nowy obiekt.