# Lists

## Steps

### 1. Create a RecyclerView
This is the element that contains the list items.
```xml
<android.support.v7.widget.RecyclerView
    android:id="@+id/itemList" />
```

### 2. Create the list item layout
```xml
<?xml version="1.0" encoding="utf-8"?>
<android.support.v7.widget.CardView xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">
    <TextView
        android:id="@+id/item_title"
    />
</android.support.v7.widget.CardView>
```

### 3. Create the item adapter

```kotlin
class ItemAdapter(private val dataset: List<Item>) : RecyclerView.Adapter<ItemAdapter.ViewHolder>() {

    class ViewHolder(val mView: View) : RecyclerView.ViewHolder(mView)

    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): ItemAdapter.ViewHolder {
        val layout = R.layout.<filename>
        val view = LayoutInflater.from(parent.context).inflate(layout, parent, false)
        return ViewHolder(view)
    }

    override fun onBindViewHolder(holder: ViewHolder, position: Int) {
        holder?.mView.item_title.text = dataset[position].title
    }

    override fun getItemCount() = dataset.size
}
```

### 4. Finally, initialize the list
```kotlin
val items = []
itemList.layoutManager = LinearLayoutManager(this.context)
itemList.adapter = ItemAdapter(items)
```

## Adding event listeners

TODO

## References

<https://developer.android.com/guide/topics/ui/layout/recyclerview>
<https://developer.android.com/reference/android/support/v7/widget/RecyclerView>
<https://www.androidhive.info/2016/01/android-working-with-recycler-view/>