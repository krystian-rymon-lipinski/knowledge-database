#tech-area/android/ble 
#status/backlog 


https://developer.android.com/guide/topics/connectivity/bluetooth/permissions - tu jest wszystko na ten temat



1) Potrzebne permisje install-time:
- BLUETOOTH
- BLUETOOTH_SCAM
- BLUETOOTH_ADMIN (API 31)
- ACCESS_COARSE_LOCATION (Android <10)
- ACCESS_FINE_LOCATION (Android +10)
2) Potrzebne permisje runtime:
- ACCESS_COARSE_LOCATION
- ACCESS_FINE_LOCATION


TODO: jak to jest z tym FINE vs. COARSE?
Before Android 10, [ACCESS_COARSE_LOCATION](https://developer.android.com/reference/android/Manifest.permission.html#ACCESS_COARSE_LOCATION) can be used to gain access to BLE scan results, but we recommend using [ACCESS_FINE_LOCATION](https://developer.android.com/reference/android/Manifest.permission.html#ACCESS_FINE_LOCATION) instead since it works for all versions of Android.

Ale na 12 nadchodzi jakieś rozróżnienie, gdzie COARSE_LOCATION może być przydatne znowu?

https://developer.android.com/guide/topics/connectivity/bluetooth/permissions#declare-android11-or-lower


###### Setup
Trzeba ściągnąć sobie referencję do odpowiedniego serwisu i do [[Android BluetoothAdapter|adaptera]]:

```kotlin
val bluetoothManager = this.getSystemService(BLUETOOTH_SERVICE) as BluetoothManager
val bluetoothAdapter = bluetoothManager.adapter
```

Poprzez adapter można brać wszystkie potrzebne rzeczy: advertiser, scanner, rozmaite state'y, adres, itp.

[[Manifest Permissions]]