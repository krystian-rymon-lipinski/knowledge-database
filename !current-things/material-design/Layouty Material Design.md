up: [[Material Design]]

**Rozmieszczenie elementów na ekranie zależy przede wszystkim od szerokości urządzenia oraz jego [[Rozdzielczość ekranów Android|rozdzielczości]]. Material Design definiuje kilka klas rozmiaru okien:**
- _compact_ - szerokość < 600 dp
- _medium_ - 600dp < szerokość < 840dp
- _expanded_ - szerokość > 840dp

Treść ekranu rozmieszczona jest w tzw. "szybach" _(ang. panes)_. Na węższych ekranach całe okno zajęte jest przez jedną, na szerszych można sobie pozwolić na wyświetlenie dwóch obok sobie. Istnieje jeszcze tryb *multi-window* - pozwala odpalić więcej aplikacji naraz, po jednej na każdym oknie.

Możliwa jest zmiana zmiana klasy rozmiaru okna podczas działania aplikacji (wskutek [[Zmiany konfiguracyjne Android|zmiany orientacji urządzenia]]). Należy wówczas rozważyć rozmieszczenie elementów na każdym z nich oraz przejście między nimi w taki sposób, by użytkownik nie gubił treści.

Material Design definiuje układy adresujące najczęściej powtarzające się potrzeby użytkowników, tak zwane [layouty kanoniczne](https://m3.material.io/foundations/layout/canonical-layouts/overview):
- lista-detal - prezentowanie listy i jej otwartego elementu na dwóch sąsiadujących, równo podzielonych szybach
- szyba wspierająca - prezentacja treści na jednej szybie oraz treści powiązanych na drugiej, mniejszej
- _feed_ - siatka wyświetlająca treści: zdjęcia, artykuły z sieci, etc.