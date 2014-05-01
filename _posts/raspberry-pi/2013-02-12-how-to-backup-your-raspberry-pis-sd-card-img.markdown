---
layout: post
comments: true
---
I noticed that there are not many decent tutorials on how to back up the Raspberry Pi's SD card image, I've decided to create a tutorial myself. :)

##1) Plug in your SD card

Standard.

##2) Find out your SD card number

Hit launchpad and search for `Disk Utility` and select it

[![image](https://www.evernote.com/shard/s13/sh/e2d349d3-b4da-427a-8e38-db4824f15637/b98db0fe711867e56f9d8ec1a9349720/deep/0/Fullscreen%2012/2/13%2012:29%20PM.jpg)](https://www.evernote.com/shard/s13/sh/e2d349d3-b4da-427a-8e38-db4824f15637/b98db0fe711867e56f9d8ec1a9349720/deep/0/Fullscreen%2012/2/13%2012:29%20PM.jpg)

After that, select your SD card.

[![image](https://www.evernote.com/shard/s13/sh/f0454a95-9207-43a9-b995-361b429685b3/d6b3bcb57ad5344f3b074cd1bb072d19/deep/0/12/2/13%2012:14%20PM.jpg)](https://www.evernote.com/shard/s13/sh/f0454a95-9207-43a9-b995-361b429685b3/d6b3bcb57ad5344f3b074cd1bb072d19/deep/0/12/2/13%2012:14%20PM.jpg)

After selecting your SD card, hit `command+i` to view more information about the SD card. Inside the window, we can find the disk identifier.

[![image](https://www.evernote.com/shard/s13/sh/37e0dcda-a792-492f-bce4-dbd9e0c1c639/001bedcf4d43d28f1958ed1ea9c6dc85/deep/0/12/2/13%2012:22%20PM.jpg)](https://www.evernote.com/shard/s13/sh/37e0dcda-a792-492f-bce4-dbd9e0c1c639/001bedcf4d43d28f1958ed1ea9c6dc85/deep/0/12/2/13%2012:22%20PM.jpg)

So in my case, it's actually `disk2`.

##3) Time for backup!

The actual command is using `dd` which I learnt from [Stackexchange](http://raspberrypi.stackexchange.com/questions/311/how-do-i-backup-my-raspberry-pi).

Note : Running this command might actually take sometime. So go grab a coffee and come back. :)

	dd if=/dev/diskx of=/path/to/image bs=1m

So in my case, I want to save it to the Desktop, hence my command will be something like

	sudo dd if=/dev/disk2 of=/Users/stevetan/Desktop/image bs=1m
	
It actually took 1553 seconds which is approximately 25 minutes to backup my whole SD card. 

[![image](https://www.evernote.com/shard/s13/sh/d2d29aa8-346e-499f-a1a1-62124ea29e11/82e0cde8c635b15e97d0df77053b551c/deep/0/Screen%20Shot%202013-02-12%20at%2012.09.05%20PM.jpg)](https://www.evernote.com/shard/s13/sh/d2d29aa8-346e-499f-a1a1-62124ea29e11/82e0cde8c635b15e97d0df77053b551c/deep/0/Screen%20Shot%202013-02-12%20at%2012.09.05%20PM.jpg)
