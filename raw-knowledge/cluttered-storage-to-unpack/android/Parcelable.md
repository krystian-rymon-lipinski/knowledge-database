#status/3-freezer 
#tech-area/android 

**Interfejs oznaczający, że jakaś klasa może zostać spakowana i rozpakowana (zserializowana i zdeserializowana) na potrzeby np. przesłania jej w Intencie lub argumencie do fragmentu.** Istnieje kilka możliwości zaimplementowania tego.

1) Poprzez plugin Gradle [[065 Kotlin-Parcelize Gradle Plugin|kotlin-parcelize]]

2) Poprzez bibliotekę [Parceler](http://parceler.org/)

**Wystarczy oznaczyć annotacją @Parcel i już!** 
Annotacje ona również procesuje.

Dependencje:
```kotlin
implementation 'org.parceler:parceler-api:1.1.12'
annotationProcessor 'org.parceler:parceler:1.1.12'
```

Użycie:
```kotlin
val wrapped = Parcels.wrap(new Example("Andy", 42));
val example: Example = Parcels.unwrap(wrapped);
example.getName(); // Andy
example.getAge(); // 42
```

Dla różnych użyć są różne wersje, np dla fragmentArgs albo intentExtras.

3) Po staremu, pisząc wszystko z palca
```kotlin
override fun describeContents(): Int {  
    return 0  //  0 lub CONTENTS_FILE_DESCRIPTOR 
}  
  
override fun writeToParcel(p0: Parcel?, p1: Int) {  
    // to tutaj zapisuje się poszczególne pola klasy
}  
  
companion object CREATOR : Parcelable.Creator<FilterDeviceParams> {  
    override fun createFromParcel(parcel: Parcel): FilterDeviceParams {  
        return FilterDeviceParams(parcel)  // tutaj odczytuje się poszczególne pola zserializowanego obiektu klasy
    }  
  
    override fun newArray(size: Int): Array<FilterDeviceParams?> {  
        return arrayOfNulls(size)  
    }  
}
```

