### Jenkins
Można robić joby albo pipeline'y. Obie te struktury robią dokładnie to samo.

Joby ustawia się konkretnie w Jenkinsie - są powiązane z konkretną isntancją Jenkinsa, tam się ustawia wszystkie parametry, co robić, kiedy, jak. Jak instancja padnie, to trochę kaplica.

Pipeline'y to po prostu skrypty pisane w Groovy. Można go gdzieś przechowywać, review'ować i przenosić między instancjami Jenkinsa.

Jenkins może skanować okresowo, żeby wykrywać zmiany w repo.
Ale generalnie repo też może powiadamiać Jenkinsa (i raczej powinno).