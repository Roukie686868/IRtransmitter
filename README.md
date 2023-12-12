# IRtransmitter
![IR Receiver/Transmitter](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-2%20(Small).jpg)

This module is equipped with 1 IR receiver and 2 IR transmitters and an ESP8266. The ESP8166 is preloaded with Tasmota-IR which lets you record and transmit IR signals. Tasmota sends and recieves information via MQTT messages (you will have to have a MQTT broker within your network) so that other software like Node Red can utilize the sensor info to interact with  equipment in your home. Controlling IR enabled equipment like TVs, ceiling fans, lighs are good use cases to interact with. Unit can be fix mounted with two screws and is powered via the USB port on the ESP8266.

## Start from pre-installed Tasmota version
The unit will come with Tasmota-IR pre-install. When it is powered up via the USB port the unit will create a hotspot with a name like tasmota-xxxxxxx-yyyy. Select this hotspot. After about 30 seconds the webpage should show up asking for WiFi details. When this webpage does apppear try to visit the unit at 192.168.4.1  
On the webpage list the WiFi Network name and password and click save. Use the tickmark to see the Wifi network password to verify it is correct.

![Network details](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-5.jpg)

Tasmota will now try to join your home network

![Tasmota tries to connect](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-6.jpg)

When successfull it will show the new IP address of the unit on your home Wifi network. Visit the device on this IP address. When an address does not show up try to find the unit on your router or use an IP scanner to find it within your home network

![Tasmota is connected](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-7.jpg)

When connected to the unit you will see the following screen.

![Tasmota Main Menu](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-8.jpg)

First configure the MQTT Network information. From the Main Menu select Configuration, select Configure MQTT, list your MQTT server IP address, the MQTT Username, MQTT Password and give the unit a Topic that properly describes its function within your network
![Tasmota Config Menu](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-9.jpg) ![](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-10.jpg) ![](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-11.jpg)

![](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-5.jpg)

![](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-5.jpg)

## Start from scratch and loadup Tasmoate first then do the setup

## examples in Node Red
