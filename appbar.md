# The App Bar

## Steps

### 1. Use a theme with no action bar
```xml
<!-- styles.xml -->
<style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
```

### 2. Create the layout
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

### 3. Set the app bar in the activity
```kotlin
setSupportActionBar(findViewById(R.id.my_toolbar))
```

## References

<https://developer.android.com/training/appbar/setting-up>
