xml-knowledge

Docs: https://www.w3.org/TR/REC-xml/

.xsd to pliki definiujące strukturę pliku xml - XML Schema Document

.xml to "zwyczajne" pliki xml

XML to język znaczników. Służy do przechowywania danych. Nie służy do opisu, jak te dane wyświetlać.
Sam z siebie XML nic nie "robi". 
Znaczniki XMLa nie są predefiniowalne - nie ma listy znaczników do używania, które robią to samo - jak w HTML.
Autor XMLa musi zdefiniować znaczniki i strukturę dokumentu.

Istnieją formaty XML dedykowane dla konkretnych "działów", np. serwisów informacyjnych lub pogodowych.
__________________________

Struktura pliku XML:

prolog

-> root element
	-> element
		-> element ...

Każdy element może mieć atrybuty. 
Każdy element może mieć zawartość tekstową.

Prolog definiuje wersję XML i kodowanie znaków.
`<?xml version="1.0" encoding="UTF-8"`			
Prolog jest opcjonalny. 


Do opisu pliku XML można używać Schemas lub DTD (Document Type Definitions)
Jeśli używa się DTD, wówczas w prologu definiuje się atrybut "standalone", który opisuje, czy DTD ma zedytować dokument uwzględniając swoje definicje.
Jeśli "standalone" = yes, to nie robi tego, jeśli no, wówczas przepatrzuje znaczniki i ewentualnie uaktualnia tenże dokument.
__________________________

Dokument XML MUSI mieć jeden "root element", który jest rodzicem dla wszystkich innych elementów.

Każdy element może zawierać:
-> tekst
-> atrybuty
-> inne elementy
-> miks wszystkich powyższych

Element może być też pusty (nie mieć wartości tekstowej), a mimo to posiadać atrybuty.
_____

Nazwy elementów ustala autor pliku - może to prowadzić do używania tych samych nazw.
W tym celu używane są przestrzenie nazw. Do nazwy elementu dodany jest prefix.

`<table>` -> `<h:table>`, o tak.



Do tworzenia zawartości plików XML służy XMLSerializer. 
I ogólnie android.util.xml.

Do odczytu zawartości plików XML służy XMLPullParser.

#tech-area/data-storage 