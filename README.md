# IRtransmitter
![IR Receiver/Transmitter](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-2%20(Small).jpg)

This module is equipped with 1 IR receiver and 2 IR transmitters and an ESP8266. The ESP8166 is preloaded with Tasmota-IR which lets you record and transmit IR signals. Tasmota sends and receives information via MQTT messages (you will have to have a MQTT broker within your network) so that other software like Node Red can utilize the sensor info to interact with  equipment in your home. Controlling IR enabled equipment like TVs, ceiling fans, lights are good use cases to interact with. Unit can be fix mounted with two screws and is powered via the USB port on the ESP8266. Setting up the unit is explained in two different ways. 1. From the preinstalled Tasmota version 2. From scratch by loading up Tasmota from the Web and then 


## Starting from pre-installed Tasmota version
The unit will come with Tasmota-IR pre-install. When it is powered up via the USB port the unit will create a hotspot with a name like tasmota-xxxxxxx-yyyy. Select this hotspot. After about 30 seconds the webpage should show up asking for WiFi details. When this webpage does appear try to visit the unit at 192.168.4.1  
On the webpage list the WiFi Network name and password and click save. Use the tick mark to see the WiFi network password to verify it is correct.

![Network details](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-5.jpg)

Tasmota will now try to join your home network

![Tasmota tries to connect](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-6.jpg)

When successful it will show the new IP address of the unit on your home WiFi network. Visit the device on this IP address. When an address does not show up try to find the unit on your router or use an IP scanner to find it within your home network.

![Tasmota is connected](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-7.jpg)

When you connect to the unit you will see the following Main Menu screen.

![Tasmota Main Menu](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-8.jpg)

First configure the MQTT Network information. From the Main Menu, select Configuration, select Configure MQTT, list your MQTT server IP address, the MQTT Username, MQTT Password and give the unit a Topic that properly describes its function within your network. Now click save. The unit will reboot and bring you back the Main Menu Screen.

![Tasmota Config Menu](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-9.jpg) ![Tasmota MQTT Menu](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-10.jpg)

Now lets configure the in and output signals. From the Main Menu select Configure and select Configure Module. In the following screen under Module type select the last option "Generic (18)" and click save. Wait for the unit to reboot.

![Tasmota GPIO Screen init](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-12.jpg)

From the Main Menu select Configure and select Configure Module once more to get back to the GPIO setting screen which should now shows all the available pins for the ESP8266. For Pin D6 GPIO12 select IRrecv from the very bottom of the list and for PIN D5 GPIO14 select IRsend (1) also at the bottom of the list. Now click save and wait again for the unit to reboot.

![Tasmota GPIO Sceen Generic 18](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-11.jpg)

From the Main Menu select Console to see what IR signal the unit is receiving. 

![Tasmota Console Screen](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-14.JPG)

## Start from scratch. Load Tasmota first then do the setup

When you want to load Tasmota yourself then visit the following website for a Web installer. https://tasmota.github.io/install/  
On the screen in the selection bar pick Tasmota-IR and click connect. A little popup show now with the available ports. Connect your ESP8266 now and see which port shows up new. Select this port and click Connect.

![Tasmota Web Installer](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-15.JPG) ![Tasmota connection Screen](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-16.JPG)

Select the Install Tasmota IR option. Set the tick mark that you want to erase the device to make sure it is completely clean before the new install. Confirm this in the next popup by clicking install

![Tasmota Web install selection](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-17.JPG) ![Tasmota Erase Devie](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-18.JPG) ![Tasmota confirm installation](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-19.JPG)

This installation take about 1 minute

![Tasmota Installing](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-20.JPG)


![Tasmota ](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-2.JPG)
![Tasmota ](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-2.JPG)
![Tasmota ](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-2.JPG)



## examples in Node Red
