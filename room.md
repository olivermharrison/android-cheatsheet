# Room Local Database

Room provides an abstraction layer over SQLite. 

There are 3 major components:
- Database
- Entity
- DAO

### Entity

```kotlin
@Entity(tableName = "items")
data class Item(
        @PrimaryKey(autoGenerate = true)
        var id : Int,
        var content: String
) {
    constructor(): this(0, "test item")
}
```

### DAO

```kotlin
@Dao
interface ItemDao {

    @Query("select * from items")
    fun getAllItems(): List<Item>

    @Insert(onConflict = REPLACE)
    fun insertItem(item: Item)
}
```

### Database

```kotlin
@Database(entities = arrayOf(Item::class), version = 1, exportSchema = false)
abstract class Database : RoomDatabase() {
    abstract fun itemDao(): ItemDao
}
```

## Initialization

```kotlin
val db = Room.databaseBuilder(this, Database::class.java,"list-master-db").build()

// add .fallbackToDestructiveMigration() to wipe DB on version change
```

Note: this should be a singleton!

## Usage

```kotlin
val items = db.itemDao().getAllItems()

// Update a recycler view
items.observe(this, Observer<List<Item>> {
    this.activity.runOnUiThread(Runnable {
        itemList.adapter = ItemAdapter(items.value!!)
    })
})
```