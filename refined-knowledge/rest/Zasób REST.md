up: [[100 REST]]

**Najmniejsza jednostka informacji w architekturze REST _(ang. resource)_.** Jego stan jest definiowany jako **reprezentacja zasobu _(ang. resource representation)_** i składa się z:
- danych
- metadanych
- linków do powiązanych zasobów

**Każdy zasób przeznaczony do interakcji klient-serwer musi mieć swój unikalny identyfikator - URI (_ang. Uniform Resource Identifier_).**

**Każdy zasób ma swój _media type_ - format danych, dzięki któremu wiadomo, w jaki sposób je procesować** (np. JSON, XML, etc.).

**Każdy zasób definiuje swoje metody _(ang. resource methods)_. Są to akcje, które można na nim wykonać** (np. ściągnąć aktualny stan, nadpisać go lub usunąć zasób). Najczęściej metody zasobu są definiowane przez metody HTTP.