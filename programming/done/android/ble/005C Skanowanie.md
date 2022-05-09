### Skanowanie
**Skanowanie w poszukiwaniu urządzeń Bluetooth.**
Potrzebne [[Manifest Permissions|permisje]]: 
- BLUETOOTH_ADMIN
- ACCESS_COARSE_LOCATION (lub inne lokalizacje w zależności od wersji Androida)

###### BluetoothAdapter#startDiscovery()
Znajduje urządzenia Bluetooth wszystkich typów - classic, Low Energy, dual i nierozpoznane. Informacje o wyskanowanych urządzeniach można dostać rejestrując [[BroadcastReceiver]] i  szukając akcji intentu:
- BluetoothDevice.ACTION_FOUND - znalezione urządzenie; szczegóły tego urządzenia (nazwa, adres, typ, itp.) w Intencie jako parcelable BluetoothDevice
- BluetoothAdapter.ACTION_DISCOVERY_STARTED
- BluetoothAdapter.ACTION_DISCOVERY_FINISHED

###### BluetoothLeScanner#startScan()
Znajduje urządzenia Low Energy, dual i nierozpoznane.
Informacje o wyskanowanych urządzeniach można dostać poprzez [[0059 ScanCallback]], który **trzeba podać** jako parametr metody _startScan()_.

Ponadto skanowanie w ten sposób pozwala definiować [[005B ScanSettings|ustawienia]] i [[005A ScanFilter|filtry]] skanowania.

---
#tech-area/android 