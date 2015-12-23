# LinkIt ONE BLE tutorial

Bluetooth Low Energy example utilizes the LinkIt ONE development board’s GATT features to manage BLE connections.

### Version
1.0.0

### Before you start

Full details on downloading and installing the Arduino IDE and LinkIt ONE SDK then configuring the IDE and upgrading the board firmware are provided in the LinkIt ONE [quick start guide].

### Understanding GATT

BLE GATT is defined by three different statements:

* Profiles: pre- defined collection of Services that has been compiled by either the Bluetooth
2
SIG or by the peripheral designers.
* Services: are used to break data up into logic entities, and contain specific chunks of data called characteristics.
* Characteristics: the lowest level concept in GATT transactions is the Characteristic, which encapsulates a single data point

![alt text][gatt]

### LinkIt ONE Hardware

For the BLE tutorial we must include to the LinkIt ONE board:
* Bluetooth antenna.
* Battery for powering.

### LinkIt ONE Arduino sketch

##### Including libraries

Sketch needs thw followings libraries for working:

* LGATTUUID.h 
* LBTServer.h

##### Sending messages using BLE

After creating the GATT profile, and declaring service and characteristics, for sending messages to master through BLE can be done using the function: **sendMessage(const char ∗str)**
```c++
setup(){
    ...
    GATTSUart uart;
    LGATTServer.begin(1, &uart);
    ...
}

loop(){
    ...
    LGATTServer.handleEvents();
    const char ∗message = ”Hello master”;
    bool msgSuccess = uart.sendMessage(message);
    ...
}
```

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)


   [quick start guide]: <http://labs.mediatek.com/site/global/developer_tools/mediatek_linkit/get-started/index.gsp>
   [gatt]: https://learn.adafruit.com/system/assets/assets/000/013/828/original/microcontrollers_GattStructure.png?1390836057 "GATT structure"


