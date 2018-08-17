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