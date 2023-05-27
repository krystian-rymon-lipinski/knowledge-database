up: [[090 Git MOC]]
#status/3-freezer
#tech-area/git 

Git trzyma stan dla każdego commita w [[Folder .git|folderze .git]].

Każdy plik jest zapisywany jest obiekt typu blob. 
Ponadto Git checksumuje każdy folder i podfolder i trzyma informacje o strukturze jako obiekt typu drzewo. 
Wreszcie tworzony jest również obiekt typu commit który posiada metadane i wskazuje na korzeń drzewa. (I wskazuje na commit poprzedni, jeśli taki istnieje. Albo na więcej commitów, jeśli powstał z merga dwóch.)

Dzięki temu Git jest w stanie odtworzyć stan plików z konkretnego commita (snapshota).
Każdy z tych obiektów ma swoją checksumę, które składają się na pełną checksumę, opisującą commit.