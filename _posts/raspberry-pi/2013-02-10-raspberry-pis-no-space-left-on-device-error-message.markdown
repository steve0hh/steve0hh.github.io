---
layout: post
comments: true
---

Today I encountered a strange error on my raspberry pi `No space left on device` error.

First possible solutions: **Expand rootfs**

In the terminal type

    sudo raspi-config

then select `expand_rootfs`

Found this solution from [here](http://www.raspberrypi.org/phpBB3/viewtopic.php?t=9210&p=118240).

Second possible method is to **update your firmware**

An easy way to do it is via [rpi-update](https://github.com/Hexxeh/rpi-update)
