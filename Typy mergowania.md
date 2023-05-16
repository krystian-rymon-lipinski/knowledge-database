up: [[Gałęzie Gita]]
#status/in-progress 
#tech-area/git 


- fast-forward - czyli Git sam przesunie wskaźnik gałęzi do której było mergowane o te commity, które do tej gałęzi dołączyły; występuje, kiedy te nowe commity w prostej linii pochodzą od gałęzi, do której było mergowane
- recursive - czyli commity na mergowanym branchu nie pochodzą wprost od commitów brancha, do którego jest mergowane - coś było w międzyczasie na masterze robione i scommitowane; wówczas trzeba znaleźć commit wspólny dla obu branchy, następnie zmergować wszystkie zmiany z głównego brancha, a potem do nich zmergować zmiany z brancha pobocznego; powstaje wówczas commit, który ma dwóch "rodziców" - wskazuje na oba miejsca, które się na niego złożyły
Recursive merging może powodować konflikty - jeżeli w obu branchach, które próbujemy połączyć, nastąpił zmiany w tych samych miejscach; wówczas w plikach, które mają konflikty pokazywane są zmiany z obu wersji poprzez znaczniki:
<<<<<<<<<<<< - początek zmian z brancha, na który wskazuje HEAD (brancha głównego, do którego było domergowywane)

=============== - przedzielenie dwóch wersji
\>>>>>>>>>>>>>>>> - koniec zmian z brancha pobocznego (tego, do którego było domergowywane)

