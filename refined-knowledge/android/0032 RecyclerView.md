up: [[010 Android MOC]]
#android/ui #android/gradle-dependency 

```groovy
implementation 'com.google.android.material:material:1.5.0' // LUB
implementation 'androidx.recyclerview:recyclerview:1.2.1'
```

**Służy do wyświetlania zbiorów danych, ale potrafi odzyskiwać widoki.**
Dzięki temu nie tworzy on 1000 widoków dla takiego rozmiaru listy, ale tworzy tylko tyle widoków, ile zmieści się na ekranie, plus kilka dodatkowych. Wówczas podczas przewijania widoki są **odzyskiwane** i wyświetlają inne dane.

**Aby wyświetlać dane w tym widoku, należy zdefiniować jego [[RecyclerView Adapter|adapter]]**.

```kotlin
recyclerView?.let {
	it.adapter = CustomAdapter() /* Adapter opisujący każdy pojedynczy widok. */
	it.layoutManager = LinearLayoutManager() /* Manager opisujący układ widoków. */
	/* Można zdefiniować własny. */
}
```

