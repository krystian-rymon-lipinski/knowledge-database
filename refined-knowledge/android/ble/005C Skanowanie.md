up: [[BLE Android API]]
#status/revision-needed (permissions outdated)

**Skanowanie w poszukiwaniu urządzeń Bluetooth.**
Potrzebne [[Manifest Permissions|permisje]]: 
- BLUETOOTH_ADMIN
- BLUETOOTH_SCAN

- ACCESS_COARSE_LOCATION (dla Androida <10)
- ACCESS_FINE_LOCATION (dla Androida >=10)

**Deklaracja permisji w Manifeście niekoniecznie załatwia sprawę. O permisje związane z lokalizacją trzeba poprosić użytkownika explicite w aplikacji!**

###### BluetoothAdapter#startDiscovery()
Znajduje urządzenia Bluetooth wszystkich typów - classic, Low Energy, dual i nierozpoznane. Informacje o wyskanowanych urządzeniach można dostać rejestrując [[BroadcastReceiver]] i  szukając akcji intentu:
- BluetoothDevice.ACTION_FOUND - znalezione urządzenie; szczegóły tego urządzenia (nazwa, adres, typ, itp.) w Intencie jako parcelable BluetoothDevice
- BluetoothAdapter.ACTION_DISCOVERY_STARTED
- BluetoothAdapter.ACTION_DISCOVERY_FINISHED

**Ten typ callbacku zwraca tylko najważniejsze informacje o urządzeniu!**
Anulowane poprzez BluetoothAdapter#cancelDiscovery()

###### BluetoothLeScanner#startScan()
Znajduje urządzenia Low Energy, dual i nierozpoznane.
Informacje o wyskanowanych urządzeniach można dostać poprzez [[0059 ScanCallback|ScanCallback]], który **trzeba podać** jako parametr metody _startScan()_.

Ponadto skanowanie w ten sposób pozwala definiować [[005B ScanSettings|ustawienia]] i [[005A ScanFilter|filtry]] skanowania.
Anulowane poprzez BluetoothLeScanned#stopScan()