#status/3-freezer 
#tech-area/http 

Dane uwierzytelniające (hasła, tokeny), dające dostęp do chronionych zasobów; serwery mogą blokować zapytania o konkretne zasoby w przypadku niezidentyfikowanego nadawcy zapytania; metod uwierzytelnienia jest wiele: hasło, token, facebook, google, certyfikat OAuth2.   

Brak uwierzytelnienia skutkuje zwrotką z błędem 401 z serwera.

1) Basic access authentication

When the user agent wants to send authentication credentials to the server, it may use the _Authorization_ header field.

The _Authorization_ header field is constructed as follows: https://en.wikipedia.org/wiki/Basic_access_authentication#cite_note-RFC7617-9

1. The username and password are combined with a single colon (:). This means that the username itself cannot contain a colon.
2. The resulting string is encoded into an octet sequence. The character set to use for this encoding is by default unspecified, as long as it is compatible with US-ASCII, but the server may suggest use of UTF-8 by sending the _charset_ parameter. https://en.wikipedia.org/wiki/Basic_access_authentication#cite_note-RFC7617-9
3. The resulting string is encoded using a variant of Base64 (+/ and with padding).
4. The authorization method and a space character (e.g. "Basic ") is then prepended to the encoded string.

For example, if the browser uses _Aladdin_ as the username and _open sesame_ as the password, then the field's value is the Base64 encoding of `Aladdin:open sesame`, or `QWxhZGRpbjpvcGVuIHNlc2FtZQ==`.
Then the _Authorization_ header field will appear as:

`Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==`

2) Bearer Token AUth

```kotlin
val authToken = "your_access_token"
val authHeaderValue = "Bearer $authToken"
```

Wszelkie inne sposoby autoryzacji muszą zostać opisane przez API serwera.