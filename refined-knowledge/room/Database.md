up: [[013.4 Room]]

**Annotacja oznaczająca klasę pełniącą funkcję bazy danych.**

Musi to być klasa abstrakcyjna rozszerzająca `RoomDatabase` oraz wymieniająca w parametrze annotacji klasy z annotacją `@Entity`, na których operuje. 
Musi również dla każdej klasy z annotacją `@Dao` definiować abstrakcyjną metodę.

```kotlin
@Database(entities = [User::class], version = 1)
abstract class AppDatabase : RoomDatabase() {
	abstract fun userDao(): UserDao
}
```