#android/ui 
#android/gradle-dependency
#status/4-liquid-nitrogen 

**Wytyczne do tworzenia [[Interfejs użytkownika|interfejsu użytkownika]].**
https://m3.material.io/

Aby wykorzystać komponenty w kodzie Androidowym, należy pobrać bibliotekę.

```kotlin
implementation("com.google.android.material:material:1.5.0")
```

Konkretne klasy i przykłady użycia są na [githubie](https://github.com/material-components/material-components-android/tree/master/docs/components).

---
Material Design korzysta z 
- kolorów
- typografii (czcionek i styli tekstu)
- kształtów
---
###### Kolory Material Design
https://m3.material.io/styles/color/the-color-system/key-colors-tones#a828e350-1551-45e5-8430-eb643e6a7713
Definiowane są trzy główne: primary, secondary tertiary w czterech różnych tonacjach.
Dodatkowo są jeszcze dwa neutralne kolory w czterech różnych tonacjach.

Paletę barw można zdefiniować poprzez [builder](https://m3.material.io/theme-builder#/custom)i eksportować go jako Theme.kt (do Compose'a) lub XML (Android Views).

Istnieją też od Androida 12 [kolory dynamiczne](https://m3.material.io/styles/color/dynamic-color/overview).

###### Typografia Material Design
Pięć grup: display, headline, title, body, label.
Każda z nich z trzema wielkościami: large, medium, small.


###### Kształty Material Design
7 grup: None, Extra-small, Small, Medium, Large, Extra-large, Full.
Są to po prostu zaokrąglenia narożników w elementach - od None będącego prostokątem, do Full nieposiadającego narożników.


---
**TextInputLayout** - pole tekstowe z obramowaniami! Można też ustawić endIcon i nie trzeba jej dodawać z palca, tylko wystarczy zdefiniować argument:

```xml
<com.google.android.material.textfield.TextInputLayout  
    style="@style/Widget.MaterialComponents.TextInputLayout.OutlinedBox"  
    ...
    app:endIconMode="clear_text">  
    <!-- "password" dla tej ikonki z przełączeniam między widocznością hasła; etc. -->
  
	<com.google.android.material.textfield.TextInputEditText        
		android:layout_width="match_parent"  
	    android:layout_height="wrap_content"  
        android:padding="16dp"  
        android:textSize="14sp" />  
  
</com.google.android.material.textfield.TextInputLayout>
```