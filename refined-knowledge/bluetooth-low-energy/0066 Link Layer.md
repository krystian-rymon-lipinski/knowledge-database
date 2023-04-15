up: [[060 Bluetooth Low Energy MOC]]

**Warstwa bezpośrednio powiązana z warstwą fizyczną. Jest implementowana jako mieszanka hardware'u i software'u.** Dokumentacja nakłada na nią ograniczenia czasowe, więc najczęściej jest ona izolowana od pozostałych warstw stosu protokołów interfejsem (Kontroler-Host Interfejs), a jej obliczenia prowadzone są na osobnym procesorze, czy wręcz na osobnym obwodzie elektrycznym.

Warstwa ta jest w stanie komunikować się z innym stosem protokołów (innym urządzeniem BLE) - jest punktem końcowym systemu (*ang. bearer)*. Udostępnia możliwości transmisji danych oraz powiadamia o ich odbiorze wyższe warstwy stosu protokołów (np. w poprzez wywoływalne procedury i callbacki).

Każdy odebrany pakiet jest sprawdzany poprzez CRC - w przypadku wykrycia błędu następuje wysłanie prośby o retransmisję. 

###### Hardware
Implementuje operacje wymagające obliczeniowo i/lub łatwo automatyzowalne, takie jak:
- generacja podstawowych elementów [[0037 Pakiet BLE|pakietu BLE]] takich jak: *preamble*, *access adress* i *CRC* 
- weryfikacja pakietu poprzez CRC
- [[air protocol framing]] (?)
- [[data whitening]] (?)
- generowanie liczb losowych
- szyfrowanie i deszyfrowanie danych (specyfikacja [[AES]])

###### Software
Definiuje [[0033 Role urządzeń BLE|rolę]] urządzenia BLE oraz stan [[0067 Połączenie BLE|połączenia]] i pozwala zmieniać jego parametry. Każde z urządzeń może być połączone z wieloma innymi, zarówno jako Master, jak i Slave. Może również spełniać różne role jednocześnie w relacji do różnych urządzeń.

**Definiuje również [[0062 Adres BLE|adres urządzenia BLE]]**.

