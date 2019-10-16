# Tabbed Navigation

## Steps

### 1. Add tabs to the AppBar

```xml
<android.support.design.widget.AppBarLayout>

    <android.support.v7.widget.Toolbar
        android:id="@+id/toolbar">
        <TextView
            android:id="@+id/toolbar_title"/>
    </android.support.v7.widget.Toolbar>

    <android.support.design.widget.TabLayout
        android:id="@+id/tabs"
        android:layout_weight="1">

        <android.support.design.widget.TabItem
            android:text="Tab 1" />

        <android.support.design.widget.TabItem
            android:text="Tab 2" />

    </android.support.design.widget.TabLayout>
</android.support.design.widget.AppBarLayout>
```

### 2. Create the ViewPager
This is the element in the activity that contains the tab content.
```xml
<android.support.v4.view.ViewPager
    android:id="@+id/tabContainer"
    app:layout_behavior="@string/appbar_scrolling_view_behavior" />
```


### 3. Initialise the tab view
```kotlin
private var mSectionsPagerAdapter: MainActivity.SectionsPagerAdapter? = null

// Create the adapter that will return a fragment for each of the primary sections of the activity.
mSectionsPagerAdapter = SectionsPagerAdapter(supportFragmentManager)

// Set up the ViewPager with the sections adapter.
tabContainer.adapter = mSectionsPagerAdapter

inner class SectionsPagerAdapter(fm: FragmentManager) : FragmentPagerAdapter(fm) {
    override fun getItem(position: Int): Fragment {
        if (position == 0) {
            // return Tab1Fragment.newInstance()
        }
        return Tab2Fragment.newInstance()
    }

    override fun getCount(): Int {
        return 1
    }
}

// listen for tab button presses
tabs.addOnTabSelectedListener( object : TabLayout.OnTabSelectedListener {
    override fun onTabSelected(tab: TabLayout.Tab) {
        tabContainer.currentItem = tab.position
    }
    override fun onTabUnselected(tab: TabLayout.Tab) {}
    override fun onTabReselected(tab: TabLayout.Tab) {}
})

// listen for swipes
tabContainer.addOnPageChangeListener(object: ViewPager.OnPageChangeListener {
    override fun onPageSelected(position: Int) {
        tabs.setScrollPosition(position, 0f, true)
    }
    override fun onPageScrollStateChanged(state: Int) { }
    override fun onPageScrolled(position: Int, positionOffset: Float, positionOffsetPixels: Int) {}
})

```


## References

<https://developer.android.com/training/implementing-navigation/lateral>


