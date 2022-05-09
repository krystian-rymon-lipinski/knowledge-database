### Android API - Bluetooth Low Energy 
**Implementacja obsługi połączenia Bluetooth z urządzeniami Low Energy.**
Opiera się na teorii [[(MOC) Bluetooth Low Energy|Bluetooth Low Energy]].

Podstawowe klasy do obsługi Bluetootha w Androidzie:
- **BluetoothManager** - zwraca stan połączenia; może też otworzyć połączenie w roli serwera. wówczas urządzenie się rozgłasza
- **BluetoothAdapter** - potrzebny, by zacząć cokolwiek związanego z BLE (rozgłaszanie, skanowanie, itp.)
---

Korzytanie z klasy **BluetoothDevice** wymaga korzystania z [[Manifest Permissions|permisji]] android.permission.BLUETOOTH

---

Android BLE error status codes
https://allmydroids.blogspot.com/2015/06/android-ble-error-status-codes-explained.html

---

Elementy implementacji:
- Rozgłaszanie
- [[005C Skanowanie|Skanowanie]]
- Connecting
- Data Exchange