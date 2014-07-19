---
layout: post
comments: true
---

So I encountered this error when I tried to login to /wp-admin, I encounter this error

    Error establishing a database connection

Well, luckily for me.. I had [W3 Total Cache](http://www.w3-edge.com/products/w3-total-cache/) installed for my site.
Hence the public area for the site are all cached and doesn't look any different.
Only the wordpress editors couln't login to mysql.


Hence I SSH-ed into the droplet to troubleshoot the error.

So I checked if mysql was running

    service mysql status

it returned

    stop: Unknown instance:

So I ran

    service mysql start



So it got me jumpy and I went on to isstall [BackupBuddy](http://ithemes.com/purchase/backupbuddy/) for my client to do a full-backup on the site in case this error occurs too often and I decide to change host.

To my horror, [BackupBuddy](http://ithemes.com/purchase/backupbuddy/) wasn't able to do a backup! My guess was that the LAMP stack was eating up too much memory, so I went around searching for an answer.

![oh god, why](http://i.imgur.com/Moc59iF.jpg)

I searched online and found a thread on [reddit](http://www.reddit.com/r/Wordpress/comments/1yrf2g/is_anyone_running_wordpress_in_a_digital_ocean/) regarding the performance for [1 clikc install wordpress on digital ocean's ubuntu 14.01 droplet](https://www.digitalocean.com/community/tutorials/one-click-install-wordpress-on-ubuntu-14-04-with-digitalocean).

![reddit comments](http://i.imgur.com/PnF0cJl.png)

It said to add swap on your droplet to solve the problems so I decided to give it a try!

I followed this [tutorial](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04).

After which, I tried to do another time do do a full backup and to my amazement, I was able to do it in less then 30 seconds!

So yeah. If you are facing a similar problem.. I hope this post helped. :)

