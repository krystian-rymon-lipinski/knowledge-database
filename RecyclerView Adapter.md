up: [[0032 RecyclerView]]
#status/revision-needed  
#tech-area/android 

**Odpowiada za dane i widok pojedynczego elementu zbioru. Musi rozszerzać klasę RecyclerView.Adapter.**

```kotlin
class CustomAdapter : RecyclerView.Adapter<CustomViewHolder>() {  
    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int) : RecyclerView.ViewHolder 
    override fun onBindViewHolder(holder: RecyclerView.ViewHolder, position: Int)  
    override fun getItemCount(): Int 
}
```

Aby odświeżyć listę widoków należy wywołać metody typu *notifyDataSetChanged()*, *notifyItemInserted()*, etc. **Generowanie wszystkich widoków jest czasochłonne i musi odbywać się na wątku UI, więc dobrze jest jak najbardziej ograniczać korzystanie z metody _notifyDataSetChanged()_!**

Wywołanie *notifyItemChanged()* spowoduje mrugnięcie widoku przy jego odświeżeniu - aby temu zapobiec, można wykorzystać [[Payloads]] do spółki z klasą [[DiffUtil]] potrzebną do przeliczenia wszystkich potrzebnych zmian w widoku listy.


Można powiązać z adapterem obiekt typu [[SortedList|SortedList]], wówczas każda zmiana na liście może zostać mu przekazana.

**RecyclerView.Adapter nie potrzebuje obiektu typu Context do ściągania zasobów!**
```kotlin
val context = holder.itemView.context
```

###### Własny ViewHolder
Służy do zdefiniowania wszystkich składników interfejsu elementu. Musi dziedziczyć po klasie RecyclerView.ViewHolder.
```kotlin
class CustomViewHolder(itemView: View) : RecyclerView.ViewHolder(itemView) { }
```
__itemView__ to główny layout elementu zbioru. Poprzez niego można odnieść się do jego składników, które zawiera (TextView, CheckBox, itp.) i ustawić ich wartość.

Można zadeklarować własny ViewHolder jako klasę wewnętrzną własnego Adaptera. (Ale nie może to być prywatna klasa wewnętrzna.)

Wszelkie listenery można zadeklarować w *onCreateViewHolder()* (to funkcja ADAPTERA!) Utworzony *holder* ma 
- składową *itemView*, poprzez którą można uzyskać dostęp do pojedynczych elementów UI, również tych, które potrzebują słuchacza. 
- składową *adapterPosition*, potrzebną do zdeterminowania, który właściwie element listy został kliknięty

Podobnie można zrobić ze wszystkimi innymi składnikami, które mają jakieś stałe zachowania. Wówczas nie trzeba tego robić w _onBindViewHolder()_ (co spowoduje robienie tego za każdym razem po podpięciu nowej zawartości do widoku).

**Ustawianie własności _alpha_ dla ViewHoldera może nie zostać wykonane przez system, ponieważ wykorzystuje on tę wartość do zasygnalizowania innych rzeczy podczas renderowania widoku.** Można albo użyć w to miejsce ustawiania kolorów albo ustawić _itemAnimator_ na null.

