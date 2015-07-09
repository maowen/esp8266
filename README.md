# ESP8266

<img src="https://olimex.files.wordpress.com/2014/08/esp8266_wi-fi_module.jpg?w=535"/>

## What is it?

Initially all the ESP8266 datasheets and documentation were in Chinese. Now, thanks to the hacker community the datasheets and SDK documentation are available in English. The SDK is very recently (June 2015) out of Beta and a number of functional libraries are available. The community has done the hard part and  the scene is ready for mere mortals to get involved!


### Features
* 802.11 b/g/n protocol
* Wi-Fi Direct (P2P), soft-AP
* Integrated TCP/IP protocol stack
* Integrated TC switch, balun, LNA, power amplifiers, and matching network
* Integrated PLI, regulators, and power management units
* +19.5dBm output power in 802.11b mode
* Integrated temperature sensor
* Supports antenna diversity
* Power down leakage current of < 10uA
* Integrated low power 32-bit CPU
* SDIO 2.0, SPI, UART
* Wake up and transmit packets in < 2ms
* Standby power consumption of < 1.0mW
* Up to 16 GPIO pins
* Small BOM - 4 capacitors, a oscillator, and an external flash.
* Nominal active WiFi power consumption ~200mA
* Small 

## Potential Applications

* Smart Power Plug
* Home Automation
* Baby Monitor
* Network Camera
* Sensor Networks
* Wearable Electronics
* Mesh Networks
* Smart IoT connected anything!

## Getting Started

### Hardware Requirements

#### For ESP-01 Module:

<img src="https://hackadaycom.files.wordpress.com/2015/03/setup1.png" width="450">

1. ESP-01 module
2. 3.3V regulator/power supply 
3. A breadboard and Dupont wires
4. USB/TTL converter
5. 1K and 2.2K resistors
6. Optionally a carrying board

## What to buy?

See [www.esp8266.com Getting Started](http://www.esp8266.com/wiki/doku.php?id=getting-started-with-the-esp8266)

###Third Party Vendor Modules

<img src="https://hackadaycom.files.wordpress.com/2014/11/esp8266.png?w=800">

See [ESP8266 Module Family](http://www.esp8266.com/wiki/doku.php?id=esp8266-module-family)

####Popular Modules
* **ESP-01**: Dupont wire friendly, very basic, exposes Rx/Tx. $3-4
* **ESP-03**: SMT, ceramic antenna, 14 exposed pins. $3-4
* **ESP-07**: SMT, ceramic antenna and socket, shielded, 16 exposed pins including ADC. $3-5
* **ESP-12**: SMT, etched-on PCB, shielded, 16 exposed pins including ADC. $4-6

## Where to buy?

###Modules
####Inexpensive

* [Electrodragon](http://www.electrodragon.com/product/esp8266-wi07c-wifi-module/)
* [Ebay Reliable US Seller](http://www.ebay.com/usr/tomyuen007) - This is who I used
* [Ebay All Sellers](http://www.ebay.com/sch/i.html?_from=R40&_nkw=esp8266&_sacat=0)

####Overpriced (but reliable?)
* [Adafruit](https://www.adafruit.com/search?q=esp8266&b=1)
* [Sparkfun](https://www.sparkfun.com/search/results?term=esp8266)
* [Seedstudio](http://www.seeedstudio.com/depot/s/esp8266.html?search_in_description=0)

###Bare Chip

* [Taobao](http://item.taobao.com/item.htm?spm=a1z10.1-c.w4004-10057817917.2.f1LTR1&id=42107731541) $1.77 + S&H

## Firmware

1. AT+ - WiFi-to-Serial bridge for external MCU
2. C/C++ - Low level but not bare metal. A ROM bootloader is used to load custom firmware and run it inside a very light OS
3. Lua
4. Micropython

By default most modules ship with the "AT" firmware

##Architecture

`int main()` is not exposed to the user. It is run and managed by the device and 
```C
void user_init (void)
{
    // Called early during device initialization
}
```

## Flashing

## WiFi Features

1. Protocols b/g/n
2. Station/Access Point/Station Point + Access Point
3. WEP/WPA/WPA2/Open Authentication
4. ROM based DHCP server

#SDK

##Architecture

Event driven software architecture. `int main()` is not exposed to the user. It is run and managed by the device. 
Here are some of the mechanisms for running your code:

* Event callbacks
* Timer driven events
* Task - limited to three with three differet priority levels
* `void user_init (void)` - Called early during device intialization


## ROM API

Comprehensive ROM commands:

1. Timers
2. System Configuration
  1. Task Scheduling
  2. Timers
  3. Power settings
  4. ADC Read
3. SPI
4. WiFi - Very easy! Hardware accelerated!
5. Over-the-Air Updates
6. Sniffer
7. SmartConfig
8. SNTP - Simple Network Time Protocol
9. TCP/UDP Sockets
10. mDNS - Multicast Domain Name System
11. AT API
12. JSON Processing
13. Peripherals - GPIO/UART/I2C/PWM

## C/C++ SDK Setup

###esp-open-sdk

Amazingly easy way to get up and running with the SDK and gcc toolchain! Thank you pfalcon!

This repository provides the integration scripts to build a complete
standalone SDK (with toolchain) for software development with the
Espressif ESP8266 and ESP8266EX chips.

https://github.com/pfalcon/esp-open-sdk

## Alternate Language Platforms
1. AT
2. Lua
3. Micropython
3. Arduino

## Software Development Resources

The vendor docs are not very extensive or thorough right now. Fortunately, wonderful people have figured things out and example code is readily available on Github.

###Community Resources

* http://www.esp8266.com/ - Useful forums and wiki. You have to dig a little to get the info but there is a lot out there.
* https://github.com/esp8266/esp8266-wiki/wiki
* https://github.com/pfalcon/esp-open-sdk
* Lots of blogs! - Just ask Google

###Espressif SDK Docs

1. SDK API Programming Guide - Overview of available ROM calls
2. IoT SDK User Manual - Info on device flashing
3. IoT SDK Demo - Overview of IoT demo code which includes some device generic info that is quite helpful. 


###Libraries

A number of libraries are freely available on Github that provide nice interfaces for the following a variety or useful protocols. I highly recommend checking out [Sming](https://github.com/anakod/Sming). Even if you do not want to use the libraries the example code is an extremely value reference.

####Sming
It is written Arduino style. Offers libraries with easy interfaces for the following protocols and more:

1. HTTP Client/Server
2. AJAX
3. Websockets
4. Mqtt
5. FTP
6. TCP/UDP Client/Server
7. GPIO/UART/I2C

###Example Code
1. SDK IoT Demo (comes with vendor SDK)
2. SDK SmartConfig (comes with vendor SDK)
3. http://github.com/esp8266/source-code-examples - Three simple examples
4. http://github.com/anakod/Sming - Awesome examples and extensive libraries. Use this!

##Demos

###Basic WiFi

View code, build, flash, serial connect

###Smart Config

Flash device, FTP the web files, Load webpage, Connect to AP

###ThingSpeak

Flash device, View Updates on ThingSpeak

###netio

Flash device, run throughput test

## Other References

* [nurdspace](https://nurdspace.nl/ESP8266)
* [Power Consumption](https://nurdspace.nl/ESP8266#Ultra-low_power_technology)
* [Hackaday](http://hackaday.com/2015/03/18/how-to-directly-program-an-inexpensive-esp8266-wifi-module/)

Flash with `esptool.py` over UART up to 454000 baud.
