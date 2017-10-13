# SonoffBoilerplate


This is a replacement firmware (Arduino IDE with ESP8266 core needed) for the ESP8266 based Sonoff devices. Use it as a starting block for customizing your Sonoff.

## Getting started
First of all you will need to solder a 4 or 5 pin header on your Sonoff so you can flash the new firmware.

You will need to download any libraries included, they should all have URLs in the source code mentioned, or you can find them in the Arduino Library Manager.

After you have the header, the libraries installed and a serial to usb dongle ready, power up the module while pressing the onboard button. This should put it into programming mode.

In the Arduino IDE for sonoff select from Tools Board Generic ESP8266 Module (installed from https://github.com/esp8266/Arduino) and set the following options:

Flash Mode: DIO
Flash Frequency: 40MHz
Upload Using: Serial
CPU Frequency: 80MHz
Flash Size: 1M (64K SPIFFS)
Debug Port: Disabled
Debug Level: None
Reset Method: ck
Upload Speed: 115200
Port: Your COM port connected to sonoff


Flash the firmware, the module should reset afterwards and the green LED should be blinking.
Slow blink = connecting
Fast blink = configuration portal started

Being your first run, connect to the Access Point the module created and configure it. If you don t get a configuration popup when connecting, open 192.168.4.1 in your browser.

After it's configured and connected, the green LED should stay lit, and the relay should be enabled (this is the default).

### Over-The-Air updates
OTA should also be enabled now and you can do future updates over the air. 
It uses the basic ArduinoOTA available in Arduino IDE port of the ESP8266 core.

### MQTT Support
MQTT has now been added
You can send messages to `deviceId/channel-0` with the following parameters:
- no parameter (blank) and the device will send it's status back
- 'on' to turn on
- 'off' to turn off
- 'toggle' to toggle between on and off
The status will come as a response on topic `deviceId/channel-0/status`

[Sonoff (ESP8266) reprogramming – Control Mains from Anywhere](https://tzapu.com/sonoff-firmware-boilerplate-tutorial/) 

[Sonoff (ESP8266) Part 2 – Control with Blynk App on iOS or Android](https://tzapu.com/sonoff-esp8266-control-blynk-ios-android/)
