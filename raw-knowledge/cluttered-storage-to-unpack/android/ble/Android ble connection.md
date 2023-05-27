#status/3-freezer 
#tech-area/android/ble 

BluetoothDevice#connectGatt() - metoda do łączenia się z urządzeniem
Ta metoda zwraca *BluetoothGatt*, na której można dokonać resztę odpytek.

*discoverServices*
*read/writeCharacteristic*
*read/writeDescriptor*

**Przy wysyłaniu czegokolwiek do Gatta, trzeba poczekać na odpowiedź i dopiero potem wysyłać następnego requesta! (A przynajmniej tak jest bezpieczniej.)**

Flaga autoconnect - 
BluetoothGattCallback:
	onConnectionStateChange:
		status - BluetoothGatt.SUCCESS i inne statusy
		state - BluetoothGatt.STATE_CONNECTED/DISCONNECTED/CONNECTING/DISCONNECTING

Trzeba najpierw znaleźć serwisy przez *onServicesDiscovered()*
A później jak coś przychodzi, to dostaje się nowe wartości przez:
*onCharacteristicRead/Write*
*onDescriptorRead/Write*
*onCharacteristicChanged*

Do ustawienia notyfikacji potrzeba dwóch rzeczy:
- setCharacteristicNotification
- writeDescriptor(0x2902) - notyfikacje 0x01, indykacje 0x10 (albo po prostu BluetoothGattDescriptor.ENABLE_NOTIFICATION_VALUE)

-----

When you create a `BluetoothGatt` object by calling `connectGatt` on a `BluetoothDevice`, you claim one of the 32 (in current Android version) available slots in the Bluetooth stack.

On this object you can now call `connect` and `disconnect` to change the state of the "goal" if Android should try to keep a connection to the device or not. Until you call `disconnect`, Android will (forever) try to connect to the device and automatically reconnect to the device if the connection drops for any reason. Calling `connect` again after `disconnect` will make it try to connect again.

Note: setting `autoConnect` to `false` in the initial `connectGatt` call will set an initial timeout for the first implicit connect attempt (usually 30 seconds), and if the device connects and the connection later drops, it won't automatically try to reconnect.

So the `BluetoothGatt` object can be in the "disconnected" state but still take up one of the 32 slots in the Bluetooth Stack. When you call `close`, you release all the resources for the `BluetoothGatt` object and return the slot to the Bluetooth stack. A close therefore implicitly also means disconnect. To potentially workaround some buggy Android devices, you could call `disconnect` on the `BluetoothGatt` object before `close`. Note that once you have called `close`, you can't call any other methods on that `BluetoothGatt` object.

Note: turning off Bluetooth means destroying all `BluetoothGatt` objects automatically.

---

Rozłączanie się z urządzeniem następuje poprzez BluetoothGatt#disconnect(), ale trzeba uważać, żeby nie wywołać od razu potem BluetoothGatt#close(). Inaczej nie wywoła się callback onConnectionStateChange, bo listener będzie już odrejestrowany. close() trzeba więc wołać z wnętrza callbacka a nie przed nim!

---

Jeszcze kwestia tego close() - zdarzało się tak, że po zakończeniu połączenia, trzeba było odczekać 1000 ms, jeśli chciało się natychmiast nawiązać nowe z tym samym urządzeniem. 

---

`BluetoothGatt.disconnect()` Disconnects an established connection, or cancels a connection attempt currently in progress.
Przy cancelowaniu próby połączenia NIE wywołuje się callback onConnectionStateChange().

---

https://stackoverflow.com/questions/38666462/android-catching-ble-connection-fails-disconnects

Here are some different scenarios

1.  device.connectGatt() -- Peripheral advertising - connection made -- followed by mBluetoothGatt.disconnect() and close().
    
    Result: this is a normal successful connection, followed by Central device closing the connection in code. Call back events are received as expected. When the Central disconnects in the code, the underlying Bluetooth Service disconnects and the Peripheral gets a Disconnection event.  
    .
    
2.  device.connectGatt() -- Peripheral advertising - connection made - followed by Peripheral switched off.
    
    Result: this is a normal successful connection, call back events as expected, followed by connection broken by Peripheral. The Peripheral indicates preferred connection supervision timeout in BleGapSvcInit and this is confirmed by Central in a Connection Parameters Update. After Peripheral drops the connection a Disconnection event occurs in Central just after the connection supervision timeout. (Repeated with 8 seconds and 4 seconds supervision timeouts).  
    .
    
3.  device.connectGatt() -- but Peripheral has stopped advertising, connection attempt allowed to time out.
    
    Result: (This is a specific scenario of the question) After 30 seconds, probably the connection timeout of the Bluetooth Service on the phone, there is a an `onConnectionStateChange` event indicating the new connection state is Disconnected - with (error) status 133. Must still remember to call `mBluetoothGatt.close()` else an interface leak occurs and subsequent connection is made on the next client interface.  
    .
    
4.  device.connectGatt() -- Peripheral still advertising but connection cancelled after 200ms using mBluetoothGatt.disconnect() and close().
    
    Result: (I found this case the most interesting, if also the most unlikely to happen in a real application) Sometimes, (about 1 in 10) the underlying Bluetooth Service actually did connect to the Peripheral; which saw a connect, followed by a disconnect; even though the App doesn't see these events in the call back. Sometimes, even though, as far as the App is concerned, the App is disconnected, the underlying Bluetooth phone service connected to the Peripheral - and remained connected in my test for a few minutes until I timed out! - and turned the BT service, or the Peripheral, off.
