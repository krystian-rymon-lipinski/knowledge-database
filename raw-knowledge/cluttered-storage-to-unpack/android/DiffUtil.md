up: [[0032 RecyclerView]]
#status/freezer 
#tech-area/android 

Algorytm porównujący dwie listy i wywołujący na adapterze odpowiednie operacje. 
**Zapobiega wywoływaniu *onNotifyDataSetChanged()*, więc jest całkiem przydatne - na przykład przy filtrowaniu lub sortowaniu. A przy tym proste. 

###### Procedura
1) Zdefiniowanie callbacka - trzeba wiedzieć, które elementy z obu list są takie same, a na których zmieniły się tylko części ich ViewHolderów.

```kotlin
private class SortDiffCallback(  
        private val oldList: List<DeviceInfoView>,  
        private val newList: List<DeviceInfoView>  
) : DiffUtil.Callback() {  
    override fun getOldListSize() = oldList.size  
    override fun getNewListSize() = newList.size  
  
    override fun areItemsTheSame(oldItemPosition: Int, newItemPosition: Int): Boolean {  
        return oldList[oldItemPosition].deviceInfo.address == newList[newItemPosition].deviceInfo.address  
    }  
  
    override fun areContentsTheSame(oldItemPosition: Int, newItemPosition: Int): Boolean {  
        return oldList[oldItemPosition].deviceInfo.isContentTheSame(newList[newItemPosition].deviceInfo)  
    }  
}
```

2) Policzenie różnic:

```kotlin
DiffUtil.calculateDiff(SortDiffCallback(oldList, newList), true)
```

3) Przekazanie do adaptera zmian:

```kotlin
mAdapter.setData(newList)
result.dispatchUpdatesTo(mAdapter)
```

Note that the RecyclerView requires you to dispatch adapter updates immediately when you change the data (you cannot defer `notify*` calls). The usage above adheres to this rule because updates are sent to the adapter right after the backing data is changed, before RecyclerView tries to read it.

**Trzeba uważać na to, jakie referencje się podaje! Jeśli te same, to DiffUtil od początku będzie operował na tych samych listach! Może być potrzebne sklonowanie list lub obiektów!**

---

Można w ogóle wspomóc się klasą robiącą to w innym wątku:
https://developer.android.com/reference/androidx/recyclerview/widget/AsyncListDiffer#submitList(java.util.List%3CT%3E)
https://medium.com/quark-works/android-asynclistdiffer-recycleviews-best-friend-365f75d84f4


---

https://developer.android.com/reference/androidx/recyclerview/widget/DiffUtil#calculateDiff(androidx.recyclerview.widget.DiffUtil.Callback,boolean)
https://developer.android.com/reference/androidx/recyclerview/widget/DiffUtil.DiffResult#dispatchUpdatesTo(androidx.recyclerview.widget.RecyclerView.Adapter)