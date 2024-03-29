up: [[013.6 Room]]

**Annotacja dla klasy definiującej tablicę bazy danych. Każda instancja tej klasy oznacza kolejny wiersz w tablicy bazy danych, a jej pola - kolumny tablicy. 

Domyślnie nazwa klasy definiuje nazwę tablicy, a nazwy pól - nazwy kolumn. Można je zmienić, podając parametry dla wybranych annotacji. Wielkość liter nie ma znaczenia.

Każda klasa definiująca tablicę MUSI definiować _PrimaryKey_ złożony z jednego lub więcej pól, dzięki któremu możliwe jest odróżnienie poszczególnych wierszy tablicy.

```kotlin
@Entity(tableName = "cutom_table_name") /* Tablica z wybraną nazwą */
data class CustomEntity(  
    @PrimaryKey val address: String, 
    @ColumnInfo(name = "soeme_column") val sideCode: Int,  
)
```

Przydatne annotacje i ich parametry:
- `@PrimaryKey` - pole będące kluczem
- `@PrimaryKey(autoGenerate = true)` - wartość klucza dla każdego wiersza generowana (inkrementowana) automatycznie; **aby zadziałało, trzeba podać w parametrze [0 lub null](https://developer.android.com/reference/android/arch/persistence/room/PrimaryKey#autogenerate)**
- `@Entity(primaryKeys = ["first", "second"]` - więcej pól składających się na klucz
- `@ColumnInfo(name = "column_name)"` - jawnie zdefiniowana nazwa kolumny
- `Ignore` - pole nietworzące kolumny w tablicy
- `@Entity(ignoredColumns = ["first", "second"]` - więcej pól nietworzących kolumn
- `ColumnInfo(index = true)` - kolumna będzie indeksowana, co może [przyspieszyć wyszukiwanie](https://www.sqlite.org/queryplanner.html)

---
https://developer.android.com/training/data-storage/room/defining-data