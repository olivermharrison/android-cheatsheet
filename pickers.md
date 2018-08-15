# Pickers

```kotlin
val cal = Calendar.getInstance()
val year = cal.get(Calendar.YEAR)
val month = cal.get(Calendar.MONTH)
val day = cal.get(Calendar.DAY_OF_MONTH)
val hour = cal.get(Calendar.HOUR_OF_DAY)
val minute = cal.get(Calendar.MINUTE)


dateTextButton.setOnClickListener {

    val dateSetListener = DatePickerDialog.OnDateSetListener { picker, year, month, day ->
        println("${year} - ${month} - ${day}")
    }

    DatePickerDialog(this, dateSetListener,year,month, day).show()
}

timeTextButton.setOnClickListener {

    val timeSetListener = TimePickerDialog.OnTimeSetListener { picker, hour, minute ->
        println("${hour}:${minute}")
    }

    TimePickerDialog(this, timeSetListener, hour, minute, true).show()
}
```