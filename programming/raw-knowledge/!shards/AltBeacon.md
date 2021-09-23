Beacon BLE, który standaryzuje Advertisement Data
https://github.com/AltBeacon/spec


BLE Advertising PDU:
1 byte - preamble
4 byte - access address
2 byte - PDU header
6 byte - AdvA
3 byte - AD Flags
***28 byte - AltBeacon Advertisement***
3 byte - CRC

**AltBeacon Advertisement**
1 byte - Advertisement Data Length - `0x1B`
1 byte - Advertisement Data Type - `0xFF`
2 byte - MFG ID - The beacon device manufacturer's company identifier code.
2 byte - Beacon Code - The big endian representation of the value `0xBEAC`
20 byte - Beacon ID - The big endian representation of the beacon identifier. For interoperability purposes, the first 16+ bytes of the beacon identifier should be unique to the advertiser's organizational unit. Any remaining bytes of the beacon identifier may be subdivided as needed for the use case.
1 byte - Ref RSSI - A 1-byte value representing the average received signal strength at 1m from the advertiser
1 byte - MFG RSVD - Reserved for use by the manufacturer to implement special features