# Pickers

## Date Picker

```kotlin
class DatePicker: DialogFragment(), DatePickerDialog.OnDateSetListener  {
    override fun onCreateDialog(savedInstanceState: Bundle?): Dialog {
        super.onCreateDialog(savedInstanceState)

        val c = Calendar.getInstance()
        val year = c.get(Calendar.YEAR)
        val month = c.get(Calendar.MONTH)
        val day = c.get(Calendar.DAY_OF_MONTH)

        return DatePickerDialog(this.activity, this, year, month, day)
    }

    override fun onDateSet(picker: DatePicker?, year: Int, month: Int, day: Int) {

    }
}
```

Usage:

```kotlin
val datePicker = DatePicker()
datePicker.show(fragmentManager, "datePicker")
```

## Time Picker

```kotlin
class TimePicker: DialogFragment(), TimePickerDialog.OnTimeSetListener {

    override fun onCreateDialog(savedInstanceState: Bundle?): Dialog {
        super.onCreateDialog(savedInstanceState)

        val c = Calendar.getInstance()
        val hour = c.get(Calendar.HOUR_OF_DAY)
        val minute = c.get(Calendar.MINUTE)

        return TimePickerDialog(this.activity, this, hour, minute, true)
    }

    override fun onTimeSet(picker: TimePicker?, hour: Int, minute: Int) {

    }
}
```

Usage: 

```kotlin
val timePicker = TimePicker()
timePicker.show(fragmentManager, "timePicker")
```