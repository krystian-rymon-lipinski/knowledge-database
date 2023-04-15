up: [[006E Operacje protokołu ATT]]

**Podczas operacji odczytu klient powinien przeparsować typ atrybutu, by poprawnie zinterpretować wartość atrybutu.**

- odczyt poprzez typ atrybutu (UUID)
- odczyt poprzez adres atrybutu
- odczyt fragmentu BLOB-a (długiego atrybutu) poprzez jego adres 
- wielokrotny odczyt - odczyt jedngo lub więcej atrybutów poprzez jego adres
- odczyt poprzez typ grupowy (UUID atrybutu jest typu grupa)