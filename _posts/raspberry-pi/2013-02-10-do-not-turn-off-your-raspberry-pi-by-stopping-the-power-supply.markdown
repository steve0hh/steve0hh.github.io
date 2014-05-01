---
layout: post
comments: true
---

**Yes. DO NOT turn it off by powering off the adapter.**

It'll cause some problems with the SD card and filesystem if the unit is still writing some files or has some unfinished process. The best way to power off the Raspberry Pi is to use this snippet of code :

    sudo shutdown -h now

Learnt it from [here](http://raspberrypi.stackexchange.com/a/383/5939).
