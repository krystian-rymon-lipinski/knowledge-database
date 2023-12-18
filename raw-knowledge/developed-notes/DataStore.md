#status/3-freezer 
#tech-area/android 
#data-storage

Zapisywanie stanu aplikacji, korzystające z [[Korutyna|korutyn]] i [[Przepływ|przepływów]]. 

Można korzystać z dwóch klas: **Preferences DataStore** i **Proto DataStore**.

```kotlin
implementation("androidx.datastore:datastore-preferences:1.0.0")
implementation("androidx.datastore:datastore:1.0.0")
```

Pierwsza opcja to pary klucz-wartość, bardzo podobna do SharedPreferences, która również nie zapewnia bezpieczeństwa typów.

```kotlin
/* DataStoreFile.kt */
val Context.currentSetDataStore by preferencesDataStore(name = "settings")
/* OtherFile.kt */
val dataStore = context.currentSetDataStore /* Zwraca DataStore<Preferences> */
dataStore.edit { /* Zapisywanie nowych wartości */ }
dataStore.data /* Zwraca Flow<Preferences> */

```

Druga opcja wymaga dodania:
- pluginu _protobuf_
- konfiguracji _protobuf_ w konfiguracji gradle
- pliku _proto_, definiującego _schema_; You need to place your `.proto` file under `_app/src/main/proto_` folder
- dodania serializera


---
https://developer.android.com/topic/libraries/architecture/datastore