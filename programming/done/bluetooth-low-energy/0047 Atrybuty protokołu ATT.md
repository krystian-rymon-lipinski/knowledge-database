### Atrybuty protokołu ATT
**Najmniejsze adresowalne jednostki danych w protokole ATT.**
**Mogą zawierać dane lub metadane (informacje o ustrukturyzowaniu danych).**

Atrybuty są zlokalizowane na urządzeniu będącym serwerem GATT - najczęściej jest to urządzenie pełniące [[0033 Role urządzeń BLE|rolę]] urządzenia peryferyjnego. Natomiast urządzenie centralne odpytuje je w celu odczytania i/lub nadpisania danych.

**Protokół ATT definiuje tylko atrybuty. [[0048 Struktury GATT|Struktury]] są konkretyzowane dopiero na poziomie protokołu GATT.**

###### Pola atrybutów
Poniższe pola występują dla każdego atrybutu:
- adres - 16-bitowy identyfikator, pozwalający odszukać dany atrybut na serwerze
- [[0053 Typ atrybutu ATT|typ]] 
- [[0046 Permisje atrybutów ATT|permisje]]
- wartość - rzeczywiste dane (lub metadane), które zawiera atrybut

###### Koncepty związane z atrybutami
- [[Cachowanie atrybutów ATT|cachowanie atrybutów]]
- [[Atrybuty ATT w danych rozgłoszeniowych|atrybuty w danych rozgłoszeniowych]]


---
#tech-area/bluetooth-low-energy 