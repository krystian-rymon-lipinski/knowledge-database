up: [[013.4 Room]]

**DAO (Database Access Object) - annotacja dla klasy definiującej operacje możliwe do wykonania na tablicy bazy danych. Może być klasą abstrakcyjną lub interfejsem.**

```kotlin
@Dao  
interface UserDao {    
	@Query("SELECT * FROM user")
	fun getAll(): List<User>

	@Query("SELECT * FROM user WHERE age > :minAge") /* Parametr włączony do zapytania SQL */
	fun getAllOlderThen(minAge: Int) : List<USer>
	
	@Insert
	fun insertAll(vararg users: User)
	
	@Delete
	fun delete(user: User)

	@Update
	fun update(user: User)
}
```

- Dla metody typu `@Query` trzeba zdefiniować zapytanie SQL. Może być ono dowolne (SELECT, INSERT, etc.).
- Można włączać parametry metody do zapytania SQL.
- Dla metod typu `@Insert/@Update/@Delete` parametry muszą być obiektami klasy oznaczonej jako `@Entity`. Parametr może być kolekcją takich obiektów, wówczas wszystkie zostaną dodane do tablicy.
- Dla metody typu `@Update` należy podać obiekt z _PrimaryKey_, który już istnieje w tablicy. W przeciwnym razie żaden z wierszy nie zostanie zaktualizowany.