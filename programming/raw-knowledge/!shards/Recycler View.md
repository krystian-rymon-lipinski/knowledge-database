### Recycler View
Służy do wyświetlania zbiorów danych, ale potrafi odzyskiwać widoki. Dzięki temu nie tworzy on 1000 widoków dla takiego rozmiaru listy, ale tworzy tylko tyle widoków, ile zmieści się na ekranie (+ kilka dodatkowych). Podczas np. przewijania widoki są **odzyskiwane** i wyświetlanie w nich inne dane.

Trzy bardzo ważne klasy:
- RecyclerView
- CustomAdapter : RecyclerView.Adapter\<CustomViewHolder>
- CustomViewHolder : RecyclerView.ViewHolder

RecyclerView
- setAdapter (adapter musi już wcześniej istnieć!)
- setLayoutManager (jak mają być wyświetlane widoki, np. w liście pionowo w dół lub jako kafelki po trzy w linii)

CustomAdapter
Musi zaimplementować 3 metody z interfejsu, który implementuje:
- onCreateViewHolder (tworzy pojedynczy widok) - tworzy go poprzez wywołanie 
```java
LayoutInflater.from(parentView.getContext()).inflate(R.layout.x, rootToAttach); /* rootToAttach jest potrzebny np. w przypadku match_parent dla widoku recyclera  */
/* Dzięki temu nie trzeba kontekstu, bo parentView może go zwrócić. */
```
- onBindViewHolder (zapisuje dane w pojedynczym widoku - korzystając z nadrzędnego layoutu, który jest zwracany w onCreateViewHolder)
- getItemCount (zwraca ilość elementów w zbiorze)

ViewHolder
To tutaj definiuje się, jakiego typu widoki chcemy wyświetlać. Np. fragmenty, LinearLayouty albo ImageView, czy cokolwiek innego.
Definiuje się tu wszystkie elementy (TextView, ImageView, itp.), które wchodzą w skład każdego z itemów listy. Można je też tutaj od razu znaleźć przez findViewById.
Jako argument w konstruktorze trzeba podać widok nadrzędny - layout, który jest nadrzędnym dla tych, które tu definiujemy. 

---

#tech-area/android 