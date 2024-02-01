up: [[013.6 Room]]

**Annotacja oznaczająca klasę pełniącą funkcję bazy danych.**

Musi to być klasa abstrakcyjna rozszerzająca `RoomDatabase` oraz wymieniająca w parametrze annotacji klasy z annotacją `@Entity`, na których operuje. 
Musi również dla każdej klasy z annotacją `@Dao` definiować abstrakcyjną metodę.

```kotlin
@Database(entities = [User::class], version = 1)
abstract class AppDatabase : RoomDatabase() {
	abstract fun userDao(): UserDao
}
```


- `exportSchema` - parametr annotacji opisujący, czy projekt powinien eksportować strukturę bazy danych do pliku, więcej w [dokumentacji](https://developer.android.com/reference/android/arch/persistence/room/Database.html#exportSchema())

```
defaultConfig {
  kapt {  
	arguments {  
	  arg("room.schemaLocation", "$projectDir/schemas")  
	}  
  }
}
```