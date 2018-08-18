# The App Bar

Firtsly, use a base theme with no action bar
```xml
<!-- styles.xml -->
<style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
```

Now create the element in the main activity layout
```xml
<android.support.design.widget.AppBarLayout
    android:gravity="center">
    <android.support.v7.widget.Toolbar
        android:id="@+id/toolbar"
        app:contentInsetStart="0dp">
        <TextView
            android:id="@+id/toolbar_title"/>
    </android.support.v7.widget.Toolbar>
</android.support.design.widget.AppBarLayout>
```

Set the app bar in the main activity
```kotlin
setSupportActionBar(findViewById(R.id.my_toolbar))
```