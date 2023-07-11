up: [[013.8 Hilt]]

**Oznaczane annotacjami `@ApplicationContext` oraz `@ActivityContext` służą do zadeklarowania odpowiedniego kontekstu jako parametru, który zostanie wstrzyknięty automatycznie przez Hilt.** Są wykorzystywane w modułach - najczęściej jako parametry metod opatrzonych jako `@Provides`.

```kotlin
@Provides  
fun provideAppDatabase(@ApplicationContext context: Context) : AppDatabase {  
    return Room.databaseBuilder(  
        context,  
        AppDatabase::class.java,  
        AppDatabase.databaseName  
    ).build()  
}
```