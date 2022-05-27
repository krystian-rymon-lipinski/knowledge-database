### RecyclerView
**Służy do wyświetlania zbiorów danych, ale potrafi odzyskiwać widoki.**
Dzięki temu nie tworzy on 1000 widoków dla takiego rozmiaru listy, ale tworzy tylko tyle widoków, ile zmieści się na ekranie, plus kilka dodatkowych. Wówczas podczas przewijania widoki są **odzyskiwane** i wyświetlają inne dane.

###### Klasa RecyclerView
Odpowiada za sam widok. Należy w nim zdefiniować jego konfigurację. 
```kotlin
recyclerView?.let {
	it.adapter = CustomAdapter() /* Adapter opisujący każdy pojedynczy widok. */
	it.layoutManager = LinearLayoutManager() /* Manager opisujący układ widoków. */
	/* Można zdefiniować własny. */
}
```

###### Własny Adapter
Odpowiada za dane i widok pojedynczego elementu zbioru. Musi implementować interfejs RecyclerView.Adapter.
```kotlin
class CustomAdapter : RecyclerView.Adapter<RecyclerView.CustomViewHolder>() {  
    override fun onCreateViewHolder(
	parent: ViewGroup, viewType: Int) : RecyclerView.ViewHolder 
	/* Tutaj definiuje się widok elementu z layoutu poprzez Inflater. */   
    override fun onBindViewHolder(holder: RecyclerView.ViewHolder, position: Int)  
	/* Tutaj zapisuje się dane do pojedynczego elementu */
    override fun getItemCount(): Int 
}
```

###### Własny ViewHolder
Służy do zdefiniowania wszystkich składników interfejsu elementu. Musi dziedziczyć po klasie RecyclerView.ViewHolder.
```kotlin
class CustomViewHolder(itemView: View) : RecyclerView.ViewHolder(itemView) { }
```
__itemView__ to główny layout elementu zbioru. Poprzez niego można odnieść się do jego składników, które zawiera (TextView, CheckBox, itp.) i ustawić ich wartość.

Można zadeklarować własny ViewHolder jako klasę wewnętrzną własnego Adaptera.
Wszelkie listenery można zadeklarować w inicjalizatorze ViewHoldera. Wówczas nie trzeba tego robić w _onBindViewHolder()_ (co spowoduje robienie tego za każdym razem po podpięciu nowej zawartości do widoku).

---
#tech-area/android 