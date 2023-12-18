up: [[013.6 Room]]
#status/2-backlog
#tech-area/data-storage


Różne annotacje pomagają.

@Embedded

@Relation

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

Przydatne w implementowaniu relacji one-to-many. Wówczas nie może istnieć w bazie obiekt tablicy B z kluczem niepasującym do żadnego obiektu z tablicy A, **również w testach!** 

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