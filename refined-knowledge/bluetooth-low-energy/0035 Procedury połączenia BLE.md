up: [[0042 Procedury urządzeń BLE]]

**Dodatkowe procedury ustanowione dla istniejącego już połączenia.**
**Może je wykonać zarówno urządzenie centralne jak i peryferyjne.**

**Name discovery** - odczytanie charakterystyki **Device Name** z [[0077 Serwis GAP|serwisu GAP]]

**Connection parameter update** - zmiana [[003F Parametry połączenia BLE|parametrów połączenia]]; urządzenie centralne może je zmienić, peryferyjne może o to jedynie poprosić, a wówczas to pierwsze decyduje, czy to zrobić; może ono zmienić parametry, ale niekoniecznie dokładnie na takie, o jakie poprosiło urządzenie peryferyjne - może też tego w ogóle nie robić

**Terminate connection** - zakończenie połączenia; może to zrobić każde z urządzeń biorących udział w komunikacji; druga strona otrzymuje wtedy liczbę-kod, opisującą przyczynę rozłączenia (np. wyjście poza zasięg połączenia lub brak sygnału od partnera przez określony czas (timeout))
