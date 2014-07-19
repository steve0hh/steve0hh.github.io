---
layout: post
comments: true
---

**Error: mysql respawning too fast, stopped**

So today I got this error in my [DigitalOcean's](https://www.digitalocean.com/?refcode=ef3f34fa0d2a) droplet using the [1-click wordpress installation for ubuntu](https://www.digitalocean.com/community/tutorials/one-click-install-wordpress-on-ubuntu-14-04-with-digitalocean).

As MySQL crashed for some unknown reason. (Most probably due to the fact that I did not create a swap for this droplet yet)

After which, I tried to restart MySQL by issuing the command via SSH:

```bash
service mysql restart
```

Output from terminal after issuing the command:

```bash
stop: Unknown instance:
start: Job failed to start
```

So I went to look at what's happening in the log with `dmesg | grep mysql` and saw this:

```bash
7642747.780843] init: mysql main process (11339) terminated with status 1
[7642747.780894] init: mysql respawning too fast, stopped
```
![mysql resawning too fast](http://i.imgur.com/gsolPVa.png)

So i went googling and saw [this thread](http://askubuntu.com/questions/127264/cant-start-mysql-mysql-respawning-too-fast-stopped).

Initially, I tried the [first answer](http://askubuntu.com/a/129143) that was marked correct but couldn't go about setting a password for root user once more.

So I decided to try my luck with the [second answer](http://askubuntu.com/a/167003) and it worked!

After I saved

```bash
innodb_buffer_pool_size = 16M
```
to the file, `/etc/mysql/my.cnf`.

I then issued `service mysql restart` and MySQL managed to restart.

After which I added a swap for my droplet which I guess will make this droplet much more stable.

Don't know if it'll be ok to remove the `innodb_buffer_pool_size` in the configuration but I am currently going to leave it there since it has no significant impact on my wordpress site's performance. :)

What do u guys think? Is it ok to remove it?

Also, I hope some of you guys wiht the same problem finds this post useful. :)

Thank you.
