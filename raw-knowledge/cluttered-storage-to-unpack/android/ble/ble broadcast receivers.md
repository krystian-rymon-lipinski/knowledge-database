#status/3-freezer 
#tech-area/android/ble 

Wykrycie zmian w lokalizacji i bluetoothie - dwóch managerach, których potrzeba do operacji BLE. Lokalizacja tylko do skanowania, bluetooth do wszystkiego. XD

```kotlin
registerReceiver(bluetoothReceiver, IntentFilter(BluetoothAdapter.ACTION_STATE_CHANGED))  
registerReceiver(locationReceiver, IntentFilter(LocationManager.PROVIDERS_CHANGED_ACTION))


private val bluetoothReceiver: BroadcastReceiver = object : BroadcastReceiver() {  
    override fun onReceive(context: Context, intent: Intent) {  
        val action = intent.action  
        if (action == BluetoothAdapter.ACTION_STATE_CHANGED) {  
            val state = intent.getIntExtra(BluetoothAdapter.EXTRA_STATE, BluetoothAdapter.ERROR)  
  
            when (state) {  
                BluetoothAdapter.STATE_ON -> viewModel.setIsBluetoothOn(true)  
                BluetoothAdapter.STATE_OFF -> viewModel.setIsBluetoothOn(false)  
                else -> { }  
            }  
        }  
    }  
}  
  
private val locationReceiver = object : BroadcastReceiver() {  
    override fun onReceive(context: Context, intent: Intent?) {  
        val locationManager = context.getSystemService(LOCATION_SERVICE) as LocationManager  
        if (intent?.action == LocationManager.PROVIDERS_CHANGED_ACTION) {  
            val state = locationManager.isProviderEnabled(LocationManager.GPS_PROVIDER)  
            viewModel.setIsLocationOn(state)  
        }  
    }  
}
```