#android/xml 
#status/3-freezer 

Można zdefiniować pliki typu drawable, żeby robiły za kształt buttona albo tła.
Można definiować różne drawable dla różnych stanów poprzez [[Android resource selector]]

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

Czasem może to nie zadziałać - niektóre elementy UI jak BottomNavigationView nie mają tego atrybutu, a poza tym foreground nie bierze pod uwagę np. zaokrąglonych narożników, o czym więcej tu: http://michaelevans.org/blog/2015/05/07/android-ripples-with-rounded-corners/.

Dla takich przypadków można zdefiniować <ripple> dla własnego drawable:

```xml
<ripple xmlns:android="http://schemas.android.com/apk/res/android"  
    android:color="?android:attr/colorControlHighlight">  <!-- KOLOR JEST KONIECZNY! -->
  
    <item android:id="@android:id/mask">  <!-- maska ripple'a -->
        <shape android:shape="rectangle">  
            <solid android:color="#000000" />  
        </shape>    
	</item>    
	<item android:drawable="@drawable/bottom_item_selector" />  <!-- customowy background -->
</ripple>
```

Ripple może zastępować selectableItemBackground (jak wyżej) lub selectableItemBackgroundBorderless (Jak niżej) - to drugie jest przydatne, gdy elementy mają paddingi lub marginesy.
https://stackoverflow.com/questions/28464983/ripple-drawable-in-xml-not-working



Można też ustawiać różne drawable w zależności od stanu poprzez [[Android resource selector|Selector]]

Albo różne drawable w zależności od poziomu poprzez [[level-list]]

Można też ustawić gradient color, jeśli nie ma być jednolity

Albo różne inne rzeczy:
https://developer.android.com/guide/topics/resources/drawable-resource
https://developer.android.com/guide/topics/resources/complex-xml-resources

---

A w ogóle to dla prostych, ale często używanych ikon (np.  w menu albo notifikacji) można użyć clip artów (zarówno jako .png i .svg). Coś w stylu strzałki wstecz albo ikonki home. Bardzo przydatne i nie trzeba robić tego po swojemu.