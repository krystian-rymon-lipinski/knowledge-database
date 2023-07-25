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