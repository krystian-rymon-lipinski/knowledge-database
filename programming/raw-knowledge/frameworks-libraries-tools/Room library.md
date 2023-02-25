Bliblioteka do tworzenia baz danych w aplikacji
https://developer.android.com/training/data-storage/room

implementation("androidx.room:room-runtime:$roomVersion")    
annotationProcessor("androidx.room:room-compiler:$roomVersion")

Architektura jest taka:

- aplikacja ściąga referencję do bazy danych.
- poprzez nią można ściągnąć referencję do tablic bazy danych (Data Access Objects)
- poprzez DAO można ściągać obiekty zapisane w bazie, dodawać je, usuwać, etc.

1) Obiekty do zapisywania w bazie, czyli Entity

```kotlin
@Entity(tableName = "bonded_devices")  /* annotacja jest konieczna, jej argument niekoniecznie */
data class BondedDevice(  
    @PrimaryKey val address: String,  /* klucz odróżniający poszczególne rekordy w bazie */
    @ColumnInfo(name = "side_code") val sideCode: Int,  
    @ColumnInfo(name = "capabilities_code") val capabilities: Int,  
    @ColumnInfo(name = "brand_code") val brand: Int,  
    @ColumnInfo(name = "sync_id") val syncId: String  
)
```

2) Obiekty tablicopodobne, które operują na Entity

```kotlin
@Dao  /* potrzebna annotacja */
interface BondedDevicesDao {  
    @Query("SELECT * FROM bonded_devices")  /* po prostu query */
    fun getAll() : List<BondedDevice>  
  
    @Insert  
    fun insert(bondedDevice: BondedDevice)  
  
    @Delete  
    fun delete(bondedDevice: BondedDevice)  
}
```

3) Obiekt bazy danych

```kotlin
@Database(entities = [User::class], version = 1)  /* klasy przechowywanych obiektów */
abstract class AppDatabase : RoomDatabase() {   
abstract fun userDao(): UserDao  /* każda z tablic musi mieć metodę, która daje zwrotkę */
}
```

4) Uzyskanie referencji do obiektu bazy danych 

```kotlin
val db = Room.databaseBuilder(applicationContext, AppDatabase::class.java, "database-name").build()
```