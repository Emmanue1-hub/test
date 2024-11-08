Below are all the functions that can be performed with the BomberCat using the programs that we have developed and that you can find in the project repository or by clicking [here](https://github.com/ElectronicCats/BomberCat/tree/main/firmware).

## Detect Tags

Below are all the functions that can be performed with the BomberCat using the programs that we have developed and that you can find in the project repository or by clicking [here](https://github.com/ElectronicCats/BomberCat/tree/main/firmware).

## Detect Tags

Example to read, write and emulate NFC cards.

It works together with the [PN7150.h](https://github.com/ElectronicCats/BomberCat/wiki/4.-First-Steps-with-Arduino#install-the-pn7150-library) library, which helps create a global NFC device interface object.

The BomberCat displays the cards it has in range as well as identifies its protocol and technology.

The BomberCat has two modes:

* **Mode 1**: Where the BomberCat reads the information from the NFC card, this mode also allows you to write information to the NFC cards. It can detect multiple NFC cards if they have the same protocol.

<p align="center">
	<img src="https://user-images.githubusercontent.com/107638696/202246891-eab575ef-a7a5-4e37-ab03-3982d3b73271.gif" width=600>
</p>

> _[Full YouTube video example - BomberCat Detect Tags](https://www.youtube.com/watch?v=2OUWNkKN-Vg&t)_

* **Mode 2**: BomberCat will emulate the NFC card, allowing you to use it as if it were the real one.
>[!IMPORTANT]
This mode is only accessible using the Wifi Web Server example.

After each reading, the configuration mode is restarted.

The NFC standards offer support for many protocols, and various types of cards can be emulated.
>[!IMPORTANT]
To know the protocols supported by this board, please click here [BomberCat/wiki/2.-BomberCat/tech-specs](https://github.com/ElectronicCats/BomberCat/wiki/2.-BomberCat#tech-specs)

## ESP32 Serial Through Flash

NINA and ESP32
Using an Arduino MCU, [serial pass-through](https://ardupilot.org/copter/docs/common-serial-passthrough.html) for flashing.

This Arduino sketch [enables you to flash](https://www.xecor.com/blog/flash-programming-basics-tools-applications) an ESP32 (through an RP2040 or comparable MCU), watch bootloader messages, and send AT commands.

Voltage level shifters must be used on the connections to ESP if the MCU is not running at 3.3V.

Though only ESP32 has been tested, the application may possibly operate on other ESPs.

Constructed and examined using an Arduino RP2040-based.

There are no guarantees that the software will run on MCUs lacking native USB.

The Visual Micro serial monitor, the Arduino serial monitor, and [PuTTY](https://www.putty.org/) in serial mode have all been used to test sending AT commands.

The same holds true for bootloader output monitoring.

ESP32's official Flash Download Tool was used to upgrade or flash the firmware.

## MagSpoof MQTT

For this example is going to be used a [MQTT Broker](https://www.emqx.com/en/blog/the-ultimate-guide-to-mqtt-broker-comparison), which serves as a centralized hub that manages and routes messages between connected clients. It operates using the publish/subscribe messaging pattern.

By simulating the electromagnetic pulses used by magnetic stripes cards, MagSpoof mode effectively simulates these cards.

It connects to a Wi-Fi network (WPA/WPA2), and creates a random client ID, then posts an announcement ("hello I'm here") on ["test.mosquitto.org"](https://test.mosquitto.org/) through port 1883. It also can be connected to an open or WEP network.


With an MQTT broker, you can check to see if it is functioning properly by entering the IP address of the BomberCart, which is shown on the serial monitor, and the port, from which you can view the message transmitted in the broker.

## MagSpoof CSV Attack.

This example included in the library allows the user to do a [CSV attack](https://medium.com/@Land2Cyber/csv-injection-a-hunters-guide-to-exploiting-spreadsheet-vulnerabilities-78e15eb10741) via MagSpoof, CSV injection occurs when malicious code is inserted into a CSV file, which can then be executed by vulnerable applications when the file is opened, to do it perform the following:
1. Upload the MagSpoof CSV attack example.
2. The BomberCat enters its mode USBMassStorage mode.
3. Drag and drop the file `dava.csv` into the BomberCat.
4. Upload the code again.
5. The CSV attack will begin.

BomberCat will send all the card's data from CSV via MagSpoof.

## WiFiWebSever
>[!IMPORTANT]
To use this example you must download and install the libraries required for this example. If you want the libraries and learn a bit more about this usage, please click here [BomberCat/firmware/WiFiWebServer](https://github.com/ElectronicCats/BomberCat/tree/main/firmware/WiFiWebServer)

Use the WiFi module of the BomberCat to create a web server that can be accessed by any device connected to the same network.

Features in this example:
* MagSpoof (spoof/emulate any magnetic stripe or credit card)
* Read NFC tags
* Emulate NFC ID
* Configure the BomberCat's WiFi network name and password.

### Setup

1. Connect your BomberCat to your computer using the USB-C cable or use a battery to turn it on.
2. Wait for the board to create the WiFi network. You should see something like this:

<p align="center">
	<img src="https://raw.githubusercontent.com/ElectronicCats/BomberCat/main/firmware/WiFiWebServer/sources/Screenshot_1.png" width=250>
</p>

3. Connect your device to the BomberCat WiFi network using the password `password`. You can change the WiFi network name and password in the `Device Config` tab of the web interface.

<p align="center">
	<img src="https://raw.githubusercontent.com/ElectronicCats/BomberCat/main/firmware/WiFiWebServer/sources/Screenshot_2.png" width=250>
</p>

4. Open a web browser and go to http://192.168.4.1. You should see the web page served by the BomberCat.

<p align="center">
	<img src="https://raw.githubusercontent.com/ElectronicCats/BomberCat/main/firmware/WiFiWebServer/sources/Screenshot_3.png" width=250>
</p>

## Client Relay NFC and Host Relay NFC.

**2 or more BomberCats are needed to perform the relay attack.**

A relay attack involves an attacker intercepting communication between two parties and relaying it to another device without examining or altering it.

With the help of this example, a BomberCat will read the desired card and transmit the information to a second BomberCat located somewhere else. The information is sent to a payment terminal or something like that by the BomberCat that receives it.

For more information watch the YouTube video [BomberCat - NFC Card relay attack](https://www.youtube.com/watch?v=BEemmRbQAz8&ab_channel=ElectronicCats)

<hr>

### Coordinator python script

This script receives requests from BomberCat clients that want 
to connect to a given BomberCat host, it also takes care of releasing 
the status of the host once the connection is terminated.

Example: use the following python script to connect to the broker named "test.mosquitto.org"

1. Open a terminal window.
2. Go through it until the directory where the script is.
3. Copy and paste the next instruction:

        python cordinator.py test.mosquitto.org
   
<p align="center">
<img src="https://github.com/user-attachments/assets/927f581f-ccae-42e9-a597-c6f121e8043a" width=750, height=150>

>[!IMPORTANT]
The coordinator script must be running before powering up both clients and hosts.    

### Host Relay NFC

To be able to enter the tracks of the magnetic band of a card, it is necessary to modify the [Arduino-SerialCommand library by @kroimon](https://github.com/kroimon/Arduino-SerialCommand).

Change in SerialCommand.h
```
// Size of the input buffer in bytes (maximum length of one command plus arguments)
#define SERIALCOMMAND_BUFFER 32
```
to
```
// Size of the input buffer in bytes (maximum length of one command plus arguments)
#define SERIALCOMMAND_BUFFER 255
```
Change in SerialCommand.cpp
```
strcpy(delim, " "); // strtok_r needs a null-terminated string
```
to
```
strcpy(delim, "-"); // strtok_r needs a null-terminated strin
```


The following commands are available in the `Host_Relay_NCF.ino` program:

    set_n: Assigns an identifier number to hosts.
    
    setup_wifi: Configures the WiFi settings, including the SSID and password.

    setup_mqtt: Configures the MQTT server settings, including the server address.

    setup_track: Allows the user to set the track data that the BomberCat will send over MQTT.

    get_config: Displays the current WiFi, MQTT, Tracks, Host and ID settings.

    help: Shows a list of available commands.


To use these commands connect the BomberCat and set the baud rate to 9600 in your serial terminal program. The user can send them using the format command-<arg0>-<arg1>-...-<argn> and press Enter key. 
    
#### Examples

To set the number of the host, the user can send the command set_n followed by the desired number.

<p align="center">
<img src="https://github.com/user-attachments/assets/22c3cf83-6e4d-44d4-a5a0-a6818fdbc974" width=750>


To set the WiFi settings, the user can send the command setup_wifi followed by the desired SSID and password.

<p align="center">
<img src="https://github.com/user-attachments/assets/5aa38805-ec99-47af-94c7-927814bae86a" width=750> 
	  
To set the MQTT settings, the user can send the command setup_mqtt followed by the desired MQTT Broker.

<p align="center">
<img src="https://github.com/user-attachments/assets/a4caaa82-949d-444f-a42e-06e00e7f18b6" width=750>

To set the tracks, the user can send the command setup_track followed by the tracks.

<p align="center">
<img src="https://github.com/user-attachments/assets/f95819e3-e6b3-4d8f-9820-1f724053d03e" width=750>

>[!IMPORTANT]
The tracks must be sent in the same line, without any space between them, looking like: %B123456781234567^LASTNAME/FIRST^YYMMSSSDDDDDDDDDDDDDDDDDDDDDDDDD?;123456781234567=112220100000000000000?

To see the current configuration, the user can send the command get_config.

<p align="center">
<img src="https://github.com/user-attachments/assets/1f55a741-6c6a-4733-9c39-7a8b6012f04e" width=750>

To look for the commands available, the user can send the command help.

<p align="center">
<img src="https://github.com/user-attachments/assets/7cee3f42-09c6-4552-b853-4e3608c73c32" width=750>
   
If an error occurs, the response to the command will be ERROR.    

<hr>
    
### Client Relay NFC

Here is a description of the commands that can be used with the Client_Relay_NFC.ino program:

    set_h: Sets the host number with which we want to establish the connection.
    free_h: Frees the current host number, allowing it to be used by another device.
    mode_nfc: Enables the NFC mode, allowing it to read NFC cards.
    mode_ms: Enables the magnetic spoof mode, allowing it to mimic the signals of a magnetic strip card.
    setup_wifi: Configures the WiFi settings, including the SSID and password.
    setup_mqtt: Configures the MQTT server settings, including the server address.
    get_config: Shows the current configuration, including the WiFi SSID, password, and MQTT server address.
    help: Shows a list of available commands.

Example: To use the BomberCat in MagSpoof mode with the magnetic band stored on host 8 the following sequence of commands would be used:
    command: mode_ms
    response: OK
    command: set_h-08
    response: OK
    response: OK
    
Example: to use the BomberCat in NFC mode a card must be inserted in host 8 and the following sequence of commands would be used:
    command: mode_nfc
    response: OK
    command: set_h-08
    response: OK
    response: OK  
    
When using a BomberCat client to request the exchange of data with an NFC card on a host, a time of 10 seconds will be counted, after which the requested host will be released.    

<hr>

### MagSpoof

Any magnetic stripe or credit card may be faked or emulated using MagSpoof.

It can work "wirelessly", even with conventional magnetic stripe and credit card readers, by producing a powerful electromagnetic field that mimics a conventional magnetic stripe card. 

Allows you to store all of your credit cards and magstripes in one device.

Works on traditional magstripe readers wirelessly.

Supports all three magnetic stripe tracks, and even supports Track 1+2 simultaneously.

<p align="center">
	<img src="https://user-images.githubusercontent.com/107638696/202248460-a83186ac-647e-4b05-9f09-fb9ab79978d5.gif" width=600>
</p>

> _[Full YouTube video example - BomberCat MagSpoof](https://www.youtube.com/watch?v=YKPMOYWtX9k&t)_
