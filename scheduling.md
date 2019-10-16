# Scheduling Alarms

<receiver
            android:name=".AlarmReceiver"
            android:enabled="true"
            android:exported="true" />

Define a BroadcastReceiver to handle the alarm:

```kotlin
class AlarmReceiver : BroadcastReceiver() {
    override fun onReceive(context: Context, intent: Intent) {
        // do something
        // val itemId = intent.getStringExtra("itemId")
    }
}
```

```kotlin
val alarm = parent.getSystemService(Context.ALARM_SERVICE) as AlarmManager
val calendar = Calendar.getInstance()
val alarmID = 1234
val aIntent = Intent(this , AlarmReceiver::class.java)
// add data: aIntent.putExtra("itemItem", alarmID.toString())
val alarmIntent = PendingIntent.getBroadcast(this, alarmID, aIntent, PendingIntent.FLAG_UPDATE_CURRENT)

// set repeating
alarm.setInexactRepeating(AlarmManager.RTC_WAKEUP, calendar.timeInMillis, AlarmManager.INTERVAL_DAY, alarmIntent)

// set once-off
alarm.set(AlarmManager.RTC_WAKEUP, calendar.timeInMillis, alarmIntent)

```


## Resetting on Device Restart

Alarms are cancelled when the device powers off, so we need to set them again when the device boots up. 

```
TODO!
```