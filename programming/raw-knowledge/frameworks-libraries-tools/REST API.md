#android/permission-needed
#status/backlog 

**Pozwala na wysyłanie requestów po http lub https. Czyli po prostu na korzystanie z internetu.**
Requesty to np. GET, PUT, POST, DELETE.

Istnieją biblioteki do obsługi zapytań HTTP po REST API, np. [[Retrofit]]

Rzeczy potrzebne:

1) Permisja do manifestu.
``<``uses-permission` `android:name``=``"android.permission.INTERNET"` `/>`
2) Wątek inny niż UI.

---
Służy do wysyłania wiadomości po HTTP. Serwer musi udostępnić swoje API, żeby wiadomo było, jak będzie wyglądała struktura zapytania, np.:

https://www.example.com/api/users - i powiedzmy, że na takie zapytanie serwer wysyła listę userów.

Struktura odpowiedzi z serwera przychodzi w formie JSON-a.

Serwery mogą oczywiście blokować poszczególne zapytania, o ile nie zidentyfikują nadawcy zapytania, np. podczas z logowaniem. 
Logowanie może się odbywać poprzez facebooka, google, etc. albo przez certyfikat OAuth2.

https://code.tutsplus.com/tutorials/android-from-scratch-using-rest-apis--cms-27117