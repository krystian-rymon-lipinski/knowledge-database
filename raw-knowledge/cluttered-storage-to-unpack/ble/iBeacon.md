up: [[BLE Beacon]]
#status/5-absolute-zero 
#tech-area/bluetooth-low-energy 

Byte 0-2: Standard BLE Flags (Not necessary but standard)

 Byte 0: Length :  0x02
 Byte 1: Type:     0x01 (Flags)
 Byte 2: Value:    0x06 (Typical Flags 0b00000110) (LE General Discoverable Mode, BR/EDR Not Supported)

Byte 3-29: Apple Defined iBeacon Data

 Byte 3: Length:             0x1a (Of the following section)
 Byte 4: Type:               0xff (Custom Manufacturer Data)
 Byte 5-6: Manufacturer ID : 0x4c00 (Apple's Bluetooth SIG registered company code, 16-bit Little Endian)
 Byte 7: SubType:            0x02 (Apple's iBeacon type of Custom Manufacturer Data)
 Byte 8: SubType Length:     0x15 (Of the rest of the iBeacon data; UUID + Major + Minor + TXPower)
 Byte 9-24: Proximity UUID        (Random or Public/Registered UUID of the specific beacon)
 Byte 25-26: Major                (User-Defined value)
 Byte 27-28: Minor                (User-Defined value)
 Byte 29: TXPower                 (8 bit Signed value, ranges from -128 to 127, use Two's Compliment to "convert" if necessary, Units: Measured Transmission Power in dBm @ 1 meters from beacon) (Set by user, not dynamic, can be used in conjunction with the received RSSI at a receiver to calculate rough distance to beacon)