# IRtransmitter
In this document the following topics  
### - Introduction
### - Starting configuring from a pre-installed Tasmota version
### - Start from scratch. Load Tasmota first then do the configuring
### - Using IR-Raw
### - Issues
### - Example in Node Red

![IR Receiver/Transmitter](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-2%20(Small).jpg)

## Introduction
This module is equipped with 1 IR receiver, 2 IR transmitters and an ESP8266. The ESP8266 is preloaded with Tasmota-IR which lets you record and transmit IR signals. Tasmota sends and receives information via MQTT messages (you will have to have a MQTT broker within your network) so that other software like Node Red can utilize the sensor info to interact with  equipment in your home. Controlling IR enabled equipment like TVs, ceiling fans, lights are good use cases. The unit can be fix mounted with two screws and is powered via the USB port on the ESP8266. Setting up the unit is explained in two different ways.  
1. From the preinstalled Tasmota version.
2. From scratch by loading up Tasmota from the Web and then configuring it as under the previous point 1.


## Starting from pre-installed Tasmota version
The unit will come with Tasmota-IR pre-installed. When it is powered up via the USB port the unit will create a hotspot with a name like **tasmota-xxxxxxx-yyyy**. Select this hotspot and after about 30 seconds a webpage should show up asking for WiFi details. When this webpage does appear try to visit the unit at 192.168.4.1  
On the webpage list the WiFi Network name and password and click save. Use the tick mark to unhide the WiFi network password to verify it is correct.

![Network details](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-5.jpg)

Tasmota will now try to join your home network

![Tasmota tries to connect](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-6.jpg)

When successful it will show the new IP address of the unit on your home WiFi network. Visit the device on this IP address in web browser. When an address does not show up try to find the unit on your router in the DHCP table or use an network IP scanner to find it within your home network.

![Tasmota is connected](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-7.jpg)

When you establish a connection to the unit you will see the following Main Menu screen.

![Tasmota Main Menu](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-8.jpg)

First configure the MQTT Network information. From the Main Menu, select **Configuration**, select **Configure MQTT**, list your MQTT server IP address, the MQTT Username, MQTT Password and give the unit a Topic that properly describes its function within your network. Now click save. The unit will reboot and bring you back the Main Menu Screen.

![Tasmota Config Menu](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-9.jpg) ![Tasmota MQTT Menu](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-10.jpg)

Now lets configure the in and output signals. From the Main Menu select **Configure** and select **Configure Module**. In the following screen under Module type select the last option "Generic (18)" and click save. Wait for the unit to reboot.

![Tasmota GPIO Screen init](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-12.jpg)

From the Main Menu select **Configure** and select **Configure Module** once more to get back to the GPIO setting screen which should now shows all the available GPIO pins for the ESP8266. For Pin D6 GPIO12 select IRrecv from the very bottom of the list and for PIN D5 GPIO14 select IRsend (1) also at the bottom of the list. Now click save and wait again for the unit to reboot.

![Tasmota GPIO Sceen Generic 18](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-11.jpg)

From the Main Menu select Console to see what IR signal the unit is receiving. 

![Tasmota Console Screen](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-14.JPG)

In a later section you can see an example how to interact and use the MQTT information.

## Start from scratch. Load Tasmota first then do the setup

When you want to load Tasmota yourself then visit the following website for the Tasmota Web installer. https://tasmota.github.io/install/  
On the screen in the selection bar pick Tasmota-IR and click connect. A little popup will shows the available ports. Connect your ESP8266 now and see which port shows up new. Select this port and click Connect. (If you had it already connected. Disconnent the ESP8266 and connect it again to see the correct port for your device)

![Tasmota Web Installer](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-15.JPG) ![Tasmota connection Screen](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-16.JPG)

Select the **Install Tasmota IR** option. In the next screen set the tick mark indicating that you want to erase the device to make sure it is completely clean before the new install. Confirm this in the next popup by clicking Install

![Tasmota Web install selection](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-17.JPG) ![Tasmota Erase Devie](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-18.JPG) ![Tasmota confirm installation](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-19.JPG)

The installation takes about 1 minute. Click **Next** once done.

![Tasmota Installing](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-20.JPG) ![Tasmota Installation Complete](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-21.JPG)

On the Configure WiFi screen select your WiFi network and enter the WiFi password and click connect.

![Tasmota Configure WiFi](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-22.JPG)

When the WiFi information was correct the unit will connect and ask you to visit the device. It should now open a new webpage with the Main Tasmota Menu. At this point you can go back the beginning of this document to work thru the settings to get the IR unit working.

![Tasmota Visit Device](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-23.JPG)


## Using IR Raw
Not all IR signals follow the standards programmed into Tasmota-IR. If your signal is not recognized then try to record the signal in RAW format.
In the Tasmota console type:  **SetOption58 1**  
and give an Enter  
0 = 	Raw data Turned Off (Default)  
1 = 	Raw data Turned On
When you enter **SetOption58 0** in the console the RAW data receiving stops again

With** SetOption38 x** the IR received protocol sensitivity can be set. By default this is set to 6.
**SetOption38 6** 

## Issues
When you have issues getting the unit to work contact me via Discord. https://discord.gg/2SuHJZ7K


## Example in Node Red

![Node Red IR example](https://github.com/Roukie686868/IRtransmitter/blob/main/Photos/IR-24.JPG)

Import the following JSON code into Node Red to get the Example
```
[
    {
        "id": "0a5249b0c0db579a",
        "type": "function",
        "z": "72cb8748.6eb078",
        "name": "Demo IR Send",
        "func": "// Following line is how you need to send a standard protocol IR signal. In this case NEC\n//msg.payload =  {\"Protocol\": \"NEC\", \"Bits\": 32, \"Data\": \"0x202B24D\", \"DataLSB\": \"0x40404DB2\", \"Repeat\": 0 }\n\nmsg.payload = { \"Protocol\": \"NEC\", \"Bits\": 32, \"Data\": \"0x202B24D\", \"DataLSB\": \"0x40404DB2\", \"Repeat\": 0 };\n\n// Following line is how you need to send a RAW IR signal in case the signal does not follow a know standard\n//msg.payload = \"0,+4515-4495+600-545+590-540E-1650C-1655CgCfEgCdEfEgCfEfEh+595fEhIdE-520+615fEfEjK-515KjKjKjKlKgIhIhClKhIlK-1660E\";\n\nreturn msg;\n",
        "outputs": 1,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 1680,
        "y": 2240,
        "wires": [
            [
                "ac883c3dcb25bbae"
            ]
        ]
    },
    {
        "id": "ac883c3dcb25bbae",
        "type": "mqtt out",
        "z": "72cb8748.6eb078",
        "name": "",
        "topic": "cmnd/office/IRSendTVRoom/irsend",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "8cbd13258d386964",
        "x": 1960,
        "y": 2240,
        "wires": []
    },
    {
        "id": "9ed9c83113a63a3d",
        "type": "inject",
        "z": "72cb8748.6eb078",
        "name": "",
        "props": [
            {
                "p": "payload"
            },
            {
                "p": "topic",
                "vt": "str"
            }
        ],
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "topic": "",
        "payload": "",
        "payloadType": "date",
        "x": 1480,
        "y": 2240,
        "wires": [
            [
                "0a5249b0c0db579a"
            ]
        ]
    },
    {
        "id": "8cbd13258d386964",
        "type": "mqtt-broker",
        "name": "MQTT .251",
        "broker": "192.168.1.251",
        "port": "1883",
        "clientid": "",
        "autoConnect": true,
        "usetls": false,
        "protocolVersion": "4",
        "keepalive": "60",
        "cleansession": true,
        "birthTopic": "",
        "birthQos": "0",
        "birthPayload": "",
        "birthMsg": {},
        "closeTopic": "",
        "closeQos": "0",
        "closePayload": "",
        "closeMsg": {},
        "willTopic": "",
        "willQos": "0",
        "willPayload": "",
        "willMsg": {},
        "userProps": "",
        "sessionExpiry": ""
    }
]
```
