**Na Androidzie da się to zrobić refleksją:**
```java
try {
  // BluetoothGatt gatt
  final Method refresh = gatt.getClass().getMethod("refresh");
  if (refresh != null) {
    refresh.invoke(gatt);
  }
} catch (Exception e) {
  // Log it
}

/* NIE ISTNIEJE ŻADEN CALLBACK, KTÓRY MÓWI, KIEDY UDA SIĘ ZREFRESHOWAĆ! */
/* DOBRZE JEST ZATEM DAĆ JAKIŚ DELAY! (500 ms wydaje się być wystarczające. */
```


---

The problem with refreshing GATT Database is related to CoreBluetooth (CB), not the app itself. The main cause is the GATT caching feature. As described [here](https://docs.silabs.com/bluetooth/latest/general/gatt-protocol/gatt-caching). There are two methods to notify peer devices about the change but on iOS, we can not use any of them directly. The CoreBluetooth framework hides some of the services, particularly the Generic Attribute Service, which is necessary in this case. We should get information about changes with proper callback from CB: [peripheral(_:didModifyServices)](https://developer.apple.com/documentation/corebluetooth/cbperipheraldelegate/1518865-peripheral), but it doesn't always work right. I've been testing it with NCP Commander to find out when it works properly. There is one regularity - it always works once! The following steps were always the same:

-   advertise with a basic NCP firmware
-   add service/characteristic or remove service/characteristic
-   refresh
-   service/characteristic appears or service/characteristic disappears in the app
-   any action (removing/adding service/characteristic)
-   refresh
-   there is no change in the iOS app - we don't get any callback, discovering services doesn't change anything

Changing GATT Database on a device more than one time always causes disappearing any information from CoreBluetooth about modifications. If we want to get a proper database inside the app, I see the following possibilities:

-   **clearing Bluetooth cache** - on iOS we have to go to Settings and reset Bluetooth manually there
-   **reconnect two times with a device** - I don't know, why it works, but it does. 

To avoid the necessity of clearing the GATT cache with one of the steps above, you have to reconnect with the device before any second modification. 

I have added the automatically refreshing GATT Database in the app after detecting any change (so calling the callback peripheral(_:didModifyServices)). As I described above, it will be called only once in one connection.

https://docs.silabs.com/bluetooth/latest/general/gatt-protocol/gatt-caching

---

