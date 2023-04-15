**Metadane opisujące operacje możliwe do wykonania na charakterystyce.**

###### Właściwości podstawowe
Zapisywane są na **1 bajcie**, gdzie każda z nich jest 1-bitową flagą.

**broadcast** - wartość charakterystyki może być użyta w [[0038 Pakiet rozgłoszeniowy BLE|pakietach rozgłoszeniowych]] jako konkretny typ [[0039 Dane rozgłoszeniowe|danych rozgłoszeniowych]]
**read** - odczytanie wartości charakterystyki
**write without response** - zapis nowej wartości do charakterystyki bez oczekiwania na potwierdzenie jej nadpisania ze strony serwera
**write** - zapis nowej wartości do charakterystyki oczekując na potwierdzenie jej nadpisania ze strony serwera
**notify** - powiadomienie ze strony serwera bez oczekiwania na potwierdzenie jego dostarczenia ze strony klienta
**indication** - powiadomienie ze strony serwera oczekując na potwierdzenie jego dostarczenia ze strony klienta
**signed write** - zapis bez odpowiedzi z dodatkowym szyfrowaniem, by potwierdzić tożsamość urządzenia żądającego zapisu

###### Właściwości dodatkowe
Ich flagi zapisywane są w [[004E Extended Properties Descriptor|dedykowanym deskryptorze]], o ile serwer GATT go posiada.

**queued write** - zapis wartości, która nie mieści się w jednym wysyłanym pakiecie
**writable auxiliaries** - dodatkowe informacje o charakterystyce, zapisywane w [[004F Characteristic User Description Descriptor|dedykowanym deskryptorze]]