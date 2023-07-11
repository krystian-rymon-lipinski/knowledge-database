#data-serialization
#data-storage

**JSON (JavaScript Object Notation) to format serializacji danych umożliwiający wymianę informacji między dwiema zainteresowanymi stronami** (np. klientem i serwerem). 

Odebranie danych od drugiej strony wymaga ich deserializacji na [[POJO|obiekty POJO]]. Można do tego użyć konwerterów: [JSON2Kotlin](https://json2kt.com/index.php), [JSON2POJO](https://www.jsonschema2pojo.org/).


Dane zapisywane są jako pary klucz-wartość, gdzie klucz to typ String. Wartości mogą być następującego typu:
- String
- liczby (całkowite lub z przecinkiem)
- wartości logiczne (true/false)
- null
- tablice; mogą one zawierać dowolny typ danych tego formatu, również tablice zagnieżdżone lub obiekty
- obiekty; mogą one zawierać dowolny typ danych tego formatu, również tablice lub obiekty zagnieżdżone

```json
{ 
	"string": "Hello, World!", 
	"number": 42, 
	"float": 3.14, 
	"boolean": true, 
	"nullValue": null, 
	"array": [1, 2, 3], 
	"object": { 
		"key": "value", 
		"nestedArray": ["a", "b", "c"],
		"nestedNumbersArray": [2, 9, 17]
	} 
}
```

Poprawność struktury można sprawdzić poprzez [walidator](https://jsonformatter.org/).

