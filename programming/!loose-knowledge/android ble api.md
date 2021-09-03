android.bluetooth API

BluetoothManager - jest po to, żeby dostać adapter

BluetoothAdapter - pozwala wykonywać podstawowe działania związane z bluetoothem
	Np. rozpoczęcie skanu, utworzenie serwera itd.
_____________________________________________

BluetoothLeAdvertiser - klasa do rozgłaszania się przez urządzenie 
	Definiuje startAdvertising() i stopAdvertising() w różnych konfiguracjach.

AdvertiseSettings - preferencje rozgłaszania się urządzenia, np. zużywając mało baterii albo przy pomocy silnego sygnału
	Istnieje Builder do definiowania instancji tej klasy.
	Cztery pola tylko: advertiseMode, connectable, timeout, txPowerLevel.

AdvertiseData - opis co zawiera pakiet danych, którym rozgłasza się urządzenie
	Istnieje Builder do definiowania instancji tej klasy.
	Manufacturer data, service UUID i ewentualnie DeviceName i TxPowerLevel.

AdvertiseCallback - callback opisujący co się wydarzy, jeśli advertising zacznie się z sukcesem lub sfailuje przy zaczynaniu



_____________________________________________

BluetoothLeScanner - klasa do poszukiwania urządzeń BLE w pobliżu 
	Może mieć różne filtry, szukać po beaconie, mocy sygnału itd.
	Wymaga callbacka.

ScanCallback - definiuje co zrobić po wyskanowaniu urządzenia
	ScanCallback#onScanResult() -> definiuje wykryte urządzenie, jako argument ma ScanResult

ScanResult - wynik skanowania, ma BluetoothDevice jako argument

BluetoothDevice - zwracane przez bluetoothowy skan - urządzenie peryferyjne

_____________________________________________

BluetoothGatt - główna klasa do połączeń, wykrywania charakterystyk, itp. 
	Urządzenie mobilne jest wówczas klientem, który może requestować o odczytanie lub zapisanie wartości z charakterystyk

	bluetoothGatt = BluetoothDevice#connectGatt()


BluetoothGattCallback - klasa reagująca na wydarzenia związane z połączeniem
	Np. zmiana charakterystyki, rozłączenie się, zapisanie wartości do charakterystyki, itp. Tutaj definiuje się reakcje na eventy.


BluetoothGattServer - klasa do połączeń
	Urządzenie mobilne jest wówczas serwerem, który ma swoje charakterystyki i je rozgłasza. Mogą one być subskrybowane przez inne urządzenia.

	bluetoothGattServer = BluetoothManager#openGattServer()

BluetoothGattServerCallback - klasa reagująca na wydarzenia związane z połączeniem
	Np. request o read czy write.
	
#tech-area/android
#tech-area/bluetooth-low-energy