---
layout: post
comments: true
---

# Wemos D1 Mini setup for OSX

**Note: This blogpost is written primarily for myself to remember how to setup a nodemcu on El Capitan**

## Lets enter the [Wemos D1 Mini](http://www.wemos.cc/Products/d1_mini.html):


## Driver

Driver for the CH340 can be found [here on wemos website](http://www.wemos.cc/downloads/).

To flash the latest [nodemcu firmware](https://github.com/nodemcu/nodemcu-firmware/releases), I used [esptool](https://github.com/themadinventor/esptool).

## Flash the firmware

```bash
esptool.py --port=/dev/tty.wchusbserialfa130  write_flash --verify -fm=dio -fs=32m 0x00000 your-path-to-node-mcu-firmware.bin
```

**Side note**

To check which port to select run the following command and choose the obvious:

```bash
ls /dev/tty.* # will return -> /dev/tty.Bluetooth-Incoming-Port /dev/tty.wchusbserialfa130
```

## Load the lua code

I am using an IDE called [ESPlorer](https://github.com/4refr0nt/ESPlorer).

Basically pretty self-explainatory to use. Will create a blogpost if you guys are interested! hit the comments!


*This blogpost will be continually be updated for commands and tools that I use for the setup*

**to be continued**
