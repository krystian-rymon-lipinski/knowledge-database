up: [[100 REST]]

**Struktura zapytań i odpowiedzi słanych przez klienta i/lub serwer w architekturze REST, w których wymiana informacji odbywa się po protokole HTTP.**

**Zapytanie:**
1. **[[Metody HTTP|Metoda HTTP]]**
2. _**Endpoint_/URL** - lokalizacja zasobu, na którym klient chce dokonać akcji; zazwyczaj jest to URL główne (aplikacji/strony) plus ścieżka dostępu do konkretnego zasobu na serwerze, np. https://www.example.com/api/users
3. **Nagłówki HTTP** - dostarczają dodatkowych informacji o zapytaniu; najczęściej używane to:
	- _Content-Type_: format zawartości zapytania, np. "application/json" dla danych typu JSON
	- autoryzacja: dane uwierzytelniające (hasła, tokeny), dające dostęp do chronionych zasobów; serwery mogą blokować zapytania o konkretne zasoby w przypadku niezidentyfikowanego nadawcy zapytania; metod uwierzytelnienia jest wiele: hasło, token, facebook, google, certyfikat OAuth2.   
	- _Accept_: oczekiwany format odpowiedzi (sformatowanie danych w konkretny sposób, np. JSON, XML, etc.)
4. **Parametry zapytania** - używane do filtrowania, sortowania, kryteriów wyszukiwania, etc.
5. **Dane zapytania _(ang. request body)_** - potrzebne dla niektórych niektóre metod (POST, PUT, etc.) wymagających wysłania danych na serwer; format danych może być różny i zależy od wymagań API serwera

**Odpowiedź:**
1. **Kod statusu** - trzycyfrowy kod opisujący rezultat przeprocesowania zapytania; znaczenie każdego z nich można znaleźć [tutaj](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
2. **Nagłówki HTTP** - dodatkowe informacje o odpowiedzi (np. _ContentType, Cache-Control_)
3. **Dane odpowiedzi _(ang. response body)_** - dane zwrócone przez serwer w konkretnym formacie