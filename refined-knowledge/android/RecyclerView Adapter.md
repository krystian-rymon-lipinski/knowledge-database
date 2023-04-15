up: [[0032 RecyclerView]]

**Odpowiada za dane i układ widoku pojedynczego elementu RecyclerView. Musi rozszerzać klasę RecyclerView.Adapter.** Dane trzymane są najczęściej w liście, układ widoku definiowany jest w [[RecyclerView ViewHolder|ViewHolderze]].

```kotlin
class CustomAdapter : RecyclerView.Adapter<CustomViewHolder>() {  
    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int) : RecyclerView.ViewHolder 
    override fun onBindViewHolder(holder: RecyclerView.ViewHolder, position: Int)  
    override fun getItemCount(): Int 
}
```

- w `onCreateViewHolder()` należy utworzyć layout widoku poprzez `LayoutInflater#inflate()`
	- można tu też zadeklarować wszelkie listenery komponentów UI (wykona się to wówczas tylko raz, a nie podczas każdego nowego bindowania widoku przy przewijaniu)
- w `onBindViewHolder()` należy ustawić wartości komponentów UI
- dostęp do danych konkretnego elementu można uzyskać poprzez `adapterPosition`; należy sprawdzać, czy aktualna pozycja nie jest równa `RecyclerView.NO_POSITION` 

Aby odświeżyć listę widoków należy wywołać metody typu *notifyDataSetChanged()*, *notifyItemInserted()*, etc. **Generowanie wszystkich widoków jest czasochłonne i musi odbywać się na wątku UI, więc dobrze jest jak najbardziej ograniczać korzystanie z metody _notifyDataSetChanged()_!**

Domyślnie odświeżenie widoku spowoduje ponowne wygenerowanie wszystkich jego składowych UI (i mrugnięcie głównego kontenera). Aby odświeżyć tylko zmieniające się elementy, należy tę zmianę przeliczyć używając klasy [[DiffUtil]] oraz zdefiniowanych [[Payloads]].
(Aby pozbyć się mrugania głównego kontenera, wystarczy dodać `Unit` jako Payloads.)

Można powiązać z adapterem obiekt typu [[SortedList|SortedList]], wówczas każda zmiana na liście może zostać mu przekazana.

