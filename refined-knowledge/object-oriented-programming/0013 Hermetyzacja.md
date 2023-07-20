up: [[031 Programowanie obiektowe]]

**Ukrywanie składowych lub metod obiektu przed obiektami innych klas.**
Osiągane poprzez modyfikatory dostępu:
- prywatny (element klasy dostępny tylko dla niej samej)
- publiczny (element klasy dostępny dla wszystkich innych klas)
- chroniony (element klasy dostępny dla klas pochodnych)
- inne (słowo-klucz i zasięg zależne od języka)

###### Składowe
**Ukrywanie składowych ma zapobiec zmianie wewnętrznego stanu obiektu przez inne obiekty.** Daje to pewność, że składowe kluczowe dla działania klasy nie zostaną w dowolnym momencie zmienione z zewnątrz.

Klasa może definiować publiczne metody, przez które dopuszcza pobieranie i modyfikowanie wartości swoich prywatnych składowych. Są to tzw. [[0023 Gettery i settery|gettery i settery]].

###### Metody
**Ukrywanie metod ma na celu wyodrębnienie funkcjonalności klasy bez przedstawiania sposobu, w jaki to robi** (zob. [[0012 Abstrakcja|abstrakcja]]). W ten sposób jedyne dostępne z zewnątrz metody to te, które wykonują określone zadania. Zakulisowe operacje potrzebne do ich wykonania są zawarte w metodach prywatnych - użytkownik nie musi o nich wiedzieć. 