up: [[RecyclerView Adapter]]
#status/3-freezer 
#tech-area/android 


https://blog.undabot.com/recyclerview-time-to-animate-with-payloads-and-diffutil-4278beb8d4dd

Trzeba się posłużyć drugą metodą onBindViewHolder - ta nie jest obowiązkowa, ale za kulisami to właśnie ona woła tę, której wymaga adapter:

```kotlin
override fun onBindViewHolder(holder: ViewHolder, position: Int, payloads: MutableList<Any>) {  
    if (payloads.isEmpty()) {  
        super.onBindViewHolder(holder, position, payloads)  
    } else {  
        holder.showChanges(payloads)  
    }  
}
```

Do wykrycia payloadów trzeba dodać metodę w klasie DiffUtil. Najprościej wziąć cały stan, żeby go później porównać i zareagować na każdą ewentualną zmianę: 

```kotlin
override fun getChangePayload(oldItemPosition: Int, newItemPosition: Int): Any {  
    return PayloadChange(oldList[oldItemPosition], newList[newItemPosition])  
}

private class PayloadChange(val oldState: T, val newState: T)

fun showChanges(payloads: List<Any>) {  
    val oldState = (payloads.first() as PayloadChange).oldState
    val newState = (payloads.last() as PayloadChange).newState 

	/* Tu zdefiniuj zmiany w widokach layoutu elementu listy */
}
```
