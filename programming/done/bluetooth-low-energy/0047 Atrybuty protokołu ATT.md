### Atrybuty protokołu ATT
**Najmniejsze adresowalne jednostki danych w protokole ATT.**
**Mogą zawierać dane lub metadane (informacje o ustrukturyzowaniu danych).**

**Protokół ATT definiuje tylko pojedyncze atrybuty. Większe [[0048 Struktury GATT|struktury]] są konkretyzowane dopiero na poziomie protokołu GATT.**

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