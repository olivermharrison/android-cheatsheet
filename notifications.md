# Notifications

## Basic Notifications

```kotlin
val mBuilder = NotificationCompat.Builder(this.context, "my-app")
    .setSmallIcon(R.drawable.notification_icon_background)
    .setContentTitle("title")
    .setContentText("content text")
    .setPriority(NotificationCompat.PRIORITY_DEFAULT)

val notificationManager = NotificationManagerCompat.from(context)
val notificationId = 1234
notificationManager.notify(notificationId, mBuilder.build())
```

## Action Buttons

Create a BroadcastReceiver to handle the action

```kotlin
class PushReceiver : BroadcastReceiver() {
    override fun onReceive(context: Context, intent: Intent) {
        val notificationId = 1234
        val action = intent.action[0]
        val notificationManager = NotificationManagerCompat.from(context)
        notificationManager.cancel(notificationId)
    }
}
```

Add the action button

```kotlin
val action = Intent(context, PushReceiver::class.java)
action.action = "my-action"
// 0 = request code... should it be unique? 
val actionIntent = PendingIntent.getBroadcast(context, 0, action, PendingIntent.FLAG_UPDATE_CURRENT)

val mBuilder = NotificationCompat.Builder(this.context, "my-app")
    .addAction(R.drawable.abc_btn_check_material, "action button", actionIntent)
```

# References

https://developer.android.com/training/notify-user/build-notification