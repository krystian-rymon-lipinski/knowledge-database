up: [[013.6 Room]]
#status/2-backlog
#tech-area/data-storage

https://developer.android.com/training/data-storage/room/relationships

### Relacja _one-to-many_

1. Tablica B musi mieć dodatkową kolumnę zawierającą wartości jednoznacznie parujące obiekty B z obiektami A (np. id).
2. Trzeba jakoś obsługiwać usuwanie obiektów B, jeśli obiekt A, od którego zależą, został usunięty. Można tego dokonać poprzez _ForeignKey_.

ForeignKey - powiązanie obiektów tablicy A, z obiektami tablicy B; jeżeli jedne są zależne od drugich (poprzez posiadanie kolumny z ID odpowiadającemu ID  drugiej tablicy), należałoby śledzić usunięcie obiektu z tablicy A, by usunąć również te z tablicy B, które były powiązane

```kotlin
@Entity(  
    tableName = SHORTCUTS_TABLE_NAME,  
    foreignKeys = [ForeignKey(  
        entity = DieEntity::class,  
        parentColumns = [DICE_TABLE_COLUMN_TIMESTAMP_ID],  
        childColumns = [SHORTCUTS_TABLE_COLUMN_DIE_ID],  
        onDelete = ForeignKey.CASCADE  
    )]  
)
```

Wówczas nie może istnieć w bazie obiekt tablicy B z kluczem niepasującym do żadnego obiektu z tablicy A, **również w testach!** 

3. Zdefiniowanie dodatkowej klasy, będącej wrapperem na oba obiekty pobieranie z bazy danych.

```kotlin
data class MatchWithGamesEntity(  
	@Embedded val matchEntity: CustomMatchEntity,  
	@Relation(  
		parentColumn = <parent_column_name>,  
		entityColumn = child_column_name  
	)  
	val games: List<CustomGameEntity>  
)
```

---

Można definiować unikalność poszczególnych kolumn:

For a single column Uniqueness

```sql
@Entity(indices = {@Index(value = {"first_name"},unique = true)})
```

For Multiple column Uniqueness

```sql
@Entity(indices = {@Index(value = {"first_name", "last_name"},unique = true)}) 
```