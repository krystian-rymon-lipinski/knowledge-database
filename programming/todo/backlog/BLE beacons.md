https://ahorasomos.izertis.com/solidgear/en/beacons-on-android/

To też urządzenie BLE, które rozgłasza swoją obecność, ale zmienia advertisement data według swojej specyfikacji, aby przekazać inne niż zazwyczaj (?) dane.
## What is exactly a beacon?

A beacon is a **hardware transmitter that broadcasts a packet information**, enabling smartphones, tablets and other electronic devices to perform specific actions when they are close to it.

The broadcasted information includes a **universally unique identifier** (UID) and several bytes that can be used to determine the device’s **physical location.**

All the beacons have the next configurable characteristics regardless the manufacturer or the protocol used:

-   **Tx power:** is the power with which the beacons transmit a signal that travels through the air and decreases with the distance. Logically, the greater is the tx power, the more battery consumes the beacon.
-   **Advertising interval:** this value defines the frequency in which the beacon emits the signal. Unlike the tx power, the lower advertising interval, the more battery consumes the beacon, but it’s important to think a bit before setting this interval value too high since the receiver device would find it more difficult to detect the beacon in this case.

## Beacons protocols
-   **[[iBeacon]]:** created by Apple, was the protocol that introduced BLE technology worldwide and defines 3 params:
    -   _UUID_: identify a group.
    -   _Major_: identify a beacons subgroup in a bigger group.
    -   _Minor_: identify a specific beacon.
-   **Eddystone:** it’s an [**open source project**](https://github.com/google/eddystone) developed by Google. Unlike iBeacon, it has official support for iOS and Android. A beacon configured with this protocol can emit one of the next packet types:
    -   _Eddystone-UID_: contains an identifier of a beacon.
    -   _Eddystone-URL_: contains an URL
    -   _Eddystone-TLM_: is emitted with the previous packets and contains the beacon health, for example, the battery life.
    -   _Eddystone-EID:_ contains an encrypted identifier that changes periodically at a rate determined during the initial registration with a web service.
-   **[[AltBeacon]]:** protocol developed by Radius Networks. It was created as an alternative to the closed protocol iBeacon, offering the same functionalities but being able to deliver more data in each message.