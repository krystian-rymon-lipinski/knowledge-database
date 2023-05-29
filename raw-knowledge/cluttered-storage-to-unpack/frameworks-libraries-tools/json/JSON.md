#tech-area/data-storage
#status/2-backlog

Ustandaryzowany format pliku, który umożliwia przesyłanie informacji między różnymi platformami
Można zamienić obiekt na JSON-owy string, a można i w drugą stronę - zamienić string z pliku na obiekty [[POJO]].

Przykład syntaxu:

```json
{
  "name": "John Smith",
  "age": 35,
  "email": "john.smith@example.com",
  "address": {
    "street": "123 Main St",
    "city": "Anytown",
    "state": "CA",
    "zip": "12345"
  },
  "phoneNumbers": [
    {
      "type": "home",
      "number": "555-1234"
    },
    {
      "type": "work",
      "number": "555-5678"
    }
  ],
  "isActive": true
}

```

https://jsonformatter.org/