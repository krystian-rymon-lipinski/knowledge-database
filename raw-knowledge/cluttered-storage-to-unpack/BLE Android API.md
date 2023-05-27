up: [[010 Android MOC]]
#status/3-freezer
#tech-area/android/ble

**Implementacja obsługi połączenia Bluetooth z urządzeniami Low Energy.**
Opiera się na teorii [[060 Bluetooth Low Energy MOC|Bluetooth Low Energy]].

Podstawowe klasy do obsługi Bluetootha w Androidzie:
- **BluetoothManager** - zwraca stan połączenia; może też otworzyć połączenie w roli serwera. wówczas urządzenie się rozgłasza
- **BluetoothAdapter** - potrzebny, by zacząć cokolwiek związanego z BLE (rozgłaszanie, skanowanie, itp.)


> [!NOTE] Dodać info o potrzebnych permissions (manifest i runtime)

---

Korzytanie z klasy **BluetoothDevice** wymaga korzystania z [[Manifest Permissions|permisji]] android.permission.BLUETOOTH

---

Android BLE error status codes
https://allmydroids.blogspot.com/2015/06/android-ble-error-status-codes-explained.html
https://medium.com/@abrisad_it/ble-error-codes-a3c6675b29c1

---

Elementy implementacji:
- Rozgłaszanie
- [[005C Skanowanie|Skanowanie]]
- Connecting
- Data Exchange