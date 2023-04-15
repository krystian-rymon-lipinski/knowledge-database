up: [[003C Typy pakietu rozgłoszeniowego]]

**Urządzenie może się rozgłaszać w różny sposób - w zależności od swego [[0034 Tryby urządzeń BLE|trybu]].** 

Mają na to wpływ trzy właściwości:
- **możliwość połączenia** 
	(1) rozgłaszające się urządzenie dopuszcza możliwość połączenia
	(0) łączenie się z urządzeniem po jego wyskanowaniu nie jest możliwe 
- **możliwość dodatkowego zapytania** 
	(1) rozgłaszające się urządzenie dopuszcza wysłanie przez skaner [[003B Scan Request|dodatkowego zapytania]]
	(0) wysyłanie dodatkowych zapytań nie jest możliwe
- **cel rozgłaszania się** 
	(1) urządzenie rozgłasza się tylko dla skanera z konkretnym adresem bluetooth; 
				dane rozgłoszeniowe muszą zawierać tylko i wyłącznie adres konkretnego skanera; 
				wymaga umożliwienia nawiązania połączenia;
	(0) urządzenie rozgłasza się dla wszystkich w zasięgu

Dzięki tym właściwościom specyfikacja definiuje następujące typy rozgłaszania:
- **ADV_IND** - 1 1 0
- **ADV_DIRECT_IND** - 1 0 1
- **ADV_NONCONN_IND** - 0 0 0 
- **ADV_SCAN_IND** - 0 1 0 

0 0 1 - zabronione, rozgłaszanie się dla konkretnego adresu wymusza umożliwienie nawiązania połączenia
0 1 1 - j.w
1 1 1 - zabronione, rozgłaszanie się dla konkretnego adresu wyklucza dodanie innych danych rozgłoszeniowych, a więc i wysłanie zapytania o dodatkowe
1 0 0 - zabronione, z jakiegoś powodu dla BLE pre-5 wszystkie urządzenia dla możliwości połączenia muszą również umożliwiać dopuszczać wysyłanie dodatkowych zapytań