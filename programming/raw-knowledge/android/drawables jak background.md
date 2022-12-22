Można zdefiniować pliki typu drawable, żeby robiły za kształt buttona albo tła.

```xml
<?xml version="1.0" encoding="utf-8"?>  
<shape xmlns:android="http://schemas.android.com/apk/res/android"  
    android:shape="rectangle" >  /* Kszałt tego czegoś. Może być kółko, owal, pierścień, prostokąt lub linia. */
  
    <solid android:color="@color/some_color" /> 
    <corners android:radius="6dp"/>  /* Zaokrąglone narożniki. */
    <stroke       
	    android:width="2dp"  
        android:color="@color/border_color" /> /* Obramowanie w kolorze. */
    <size /> /* Rozmiar */
  
</shape>
```

Żeby ustawić ten kształt jako background wystarczy:

android:background="@drawable/custom_drawable"

Ustawienie backgroundu może spowodować, że buttony nie będą się zachowywały standardowo po kliknięciu (nie będzie animacji potwierdzającej klik). Wówczas trzeba dodać:

```xml
android:foreground="?attr/selectableItemBackground"  
android:clickable="true"
```

	

Można też ustawiać różne drawable w zależności od stanu poprzez [[Android resource selector|Selector]]

Albo różne drawable w zależności od poziomu poprzez [[level-list]]

Można też ustawić gradient color, jeśli nie ma być jednolity

Albo różne inne rzeczy:
https://developer.android.com/guide/topics/resources/drawable-resource

---

A w ogóle to dla prostych, ale często używanych ikon (np.  w menu albo notifikacji) można użyć clip artów (zarówno jako .png i .svg). Coś w stylu strzałki wstecz albo ikonki home. Bardzo przydatne i nie trzeba robić tego po swojemu.