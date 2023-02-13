### Hackathon - retrospektywa

###### 1) Środowisko chmurowe

Pierwszy raz używane, tu akurat Azure.
Różne potrzebne narzędzia - code repository, kanban boards, CI pipelines.


DevOps to właśnie ogarnianie projektu jako całości i narzędzi do niego.
FinOps to optymalizowanie kosztów używania zasobów chmurowych.


###### 2) Wykorzystane technologie

a) REST API
Służy do wysyłania wiadomości po HTTP. Serwer musi udostępnić swoje API, żeby wiadomo było, jak będzie wyglądała struktura zapytania, np.:

https://www.example.com/api/users - i powiedzmy, że na takie zapytanie serwer wysyła listę userów.

Struktura odpowiedzi z serwera przychodzi w formie JSON-a.

Serwery mogą oczywiście blokować poszczególne zapytania, o ile nie zidentyfikują nadawcy zapytania, np. podczas z logowaniem. 
Logowanie może się odbywać poprzez facebooka, google, etc. albo przez certyfikat OAuth2.

b) Retrofit - biblioteka do REST API 
Można w nim zapiąć konwerter konkretnego parsowania obiektow typu JSON, np. GSON.

c) JSON - ustandaryzowany format pliku, który umożliwia przesyłanie informacji między różnymi platformami
Można zamienić obiekt na JSON-owy string, a można i w drugą stronę - zamienić string z pliku na obiekty POJO.

d) GSON - biblioteka do parsowania obiektów z i do formatu JSON

d) POJO - Plain Old Java Object - obiekt, ktory ma za zadanie modelować dane w aplikacji - w kotlinie jest to po prostu 'data class'
W internecie istnieją konwertery JSON-a na POJO.

e) Google Maps
Udostępnia swoje API i mają fajne snippety, które opisują różne use case'y.
Jednym z tych API jest REST-owe API, przez które można z serwerów Google'a ściągnąć potrzebne informacje na temat konkretnego obszaru mapy - długość i szerokość geograficzną i różne miejsca w okolicy.

###### 3) Inne rzeczy przydatne w projekcie
a) pipeline w CI w Azure pisany w **YAML-u** - języku do serializacji i zachowywania danych w pliku (trochę jak JSON, są one kompatybilne od wersji 1.2 YAML-a)
b) Swagger - framework do generowania REST-owego API - daje względne ścieżki zapytania, parametry oraz JSON-a, którego dostaje się w odpowiedzi
c) https://json2kt.com/ - konwerter pliku typu JSON na obiekty POJO (umożliwia deserializację)
d) figma - tool do designu? chyba?

###### 4) Rzeczy do zrobienia poza tym
- Android: ConstraintLayout
- Android: ViewBinding
- Android: Fragments
- Git - Basics (i.e. - user.name & user.email)
- Git - Stash
- Android Studio - setup (shortcuts, window modes, etc.)

###### 5) Inne biblioteki
- Android Material Design
- Room (do stashowania rzeczy?)
