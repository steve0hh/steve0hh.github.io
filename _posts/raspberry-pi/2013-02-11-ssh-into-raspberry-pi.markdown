---
layout: post
comments: true
---
As many have known, there is this super simple way. And it is? via SSH!

If you prefer configuring your RPi with command line, like me, this is the way to go! So below are a few simple steps on how you do it.

Note :

- This commands were learnt from [elinux.org](http://elinux.org/RPi_Remote_Access).
- This guide is written with the fact that all the commands were using the Raspbian ?wheezy? image. | [Download page](www.raspberrypi.org/downloads) | [torrent](http://downloads.raspberrypi.org/images/raspbian/2012-12-16-wheezy-raspbian/2012-12-16-wheezy-raspbian.zip.torrent) | [direct link](http://downloads.raspberrypi.org/images/raspbian/2012-12-16-wheezy-raspbian/2012-12-16-wheezy-raspbian.zip).

##1) Knowing your Raspberry Pi's IP address
As you might be thinking, we can't even see anything from the Pi, how do we even know what is the IP address of our Pis?
Well, it's pretty simple. If you are using a router, just connect the Pi up to the router! Then check the Router's log.
Here's how I did it?

Connect RPi to the router
[![image](http://i.imgur.com/9nPnwKF.jpg)](http://i.imgur.com/9nPnwKF.jpg)

Then access router's control panel, we'll go to the browser's address bar and type in the router's IP address.

[View here if you do not know how to get your router's IP address](http://superuser.com/questions/205556/how-to-find-out-ip-address-of-router/205589#205589).

[![image](http://i.imgur.com/gUqlT0q.png)](http://i.imgur.com/gUqlT0q.png)


This will be the page displayed.
[![image](http://i.imgur.com/Umx5YRm.png)](http://i.imgur.com/Umx5YRm.png)

Access the system log / console.

[![image](http://i.imgur.com/5J4EIt5.png)](http://i.imgur.com/5J4EIt5.png)

In the system log, serach for

    raspberrypi

In that, normally you would see the IP address with it, below is an example.

[![image](http://i.imgur.com/7wsw4J8.png)](http://i.imgur.com/7wsw4J8.png)

##2) Now SSH into it via command line! :)

    ssh <ip address of your Rpi> -l <username of RPi user you set up previously>

in my case it will be

    ssh 192.168.1.6 -l pi

##3) Clear the public and private keys
This part is totally optional but highly recommended, due to the fact that that everyone that downloads the Raspbian ?wheezy? image, they will have the same public & private key, hence it's better to generate your own, preventing man-in-the-middle attacks. 

So in the SSH console type (Don't worry, it won't break your SSH connection) :

    sudo rm /etc/ssh/ssh_host_*

    sudo dpkg-reconfigure openssh-server

After you generate your own keys, the next time you log in you'll have to clean up your client's known_hosts in order to log in.
