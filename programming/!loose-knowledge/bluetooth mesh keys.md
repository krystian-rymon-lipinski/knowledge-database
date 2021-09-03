Types of keys in bluetooth mesh (3.8.6)

-> DeviceKey (for a single node)
-> ApplicationKey (for a group of nodes)
-> NetworkKey (for a network)

A node may have knowledge about SINGLE DeviceKey and MULITPLE GroupKeys and NetKeys.

ApplicationKey can be used only with ONE NetKey. NetKey might have more AppKeys bound to it. 

Multiple ApplicationKeys can be bound to a model.

#tech-area/bluetooth-low-energy/bluetooth-mesh 