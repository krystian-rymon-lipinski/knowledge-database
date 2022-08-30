### LiveData
**Pojemniki na dane, które są również obiektami obserwowanymi. Ich Obserwatorami są kontrolery UI (aktywności, fragmenty).**  

Respektują one cykl życia kontrolerów UI w taki sposób, że powiadamiają o zmianie stanu tyle te, które są aktywne.

###### Tworzenie 
```kotlin
val field1 = LiveData<Int>()
val field2 = MutableLiveData(false) /* inicjalizacja wartością */
```

Zainicjowanie LiveData wartością od razu przy deklaracji spowoduje, że po zasubskrybowaniu się na nią obserwator zostanie powiadomiony o tej wartości.

Wartości MutableLiveData można zmieniać z zewnątrz poprzez:
- setValue - musi zostać wywołane na głównym wątku
- postValue - może zostać wywołane z innych wątków

###### Wykorzystywanie
Każde pole jest obiektem obserwowanym, a kontroler UI obserwuje te, na które się zapisał.

```kotlin
viewModel.field.observe(this, Observer { /* wersja dla aktywności */
	// field value changed, do something
})
viewModel.field.observe(viewLifecycleOwner, Observer { /* wersja dla fragmentu */ 
    // field value changed, do something
})
```

Zamiast obserwować zmiany w kontrolerze UI można zdefiniować obserwatory LiveData bezpośrednio w widokach xml poprzez [[Data Binding|Data Binding]].

---
#tech-area/android 