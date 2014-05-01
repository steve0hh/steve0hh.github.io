---
layout: post
comments: true
---

Recently I've searched for tutorials on how to set up sencha touch code assist on aptana. But I've only found a [forum post](http://www.sencha.com/forum/showthread.php?112540-Aptana-Code-Assist-for-Sencha-Touch&s=8e5be793e1b19daba312a0ce442503ea) on that.
Hence, I've decided to write a tutorial to do it based on it. :>

1) In Aptana Studio, go to Help -> Install New Software

![Help -> Install New Software](http://i.imgur.com/1GnZjBS.png)

2) Click "Add" to add a repository
* Name: Spket IDE
* Location: [http://www.agpad.com/update/](http://www.agpad.com/update/)

![](http://i.imgur.com/JdkK1h8.png)

![](http://i.imgur.com/fUR9Por.png)

3) A list will appear wit 3 repository for Spket IDE. (Spket IDE, Spket Text Editor and Xerces for Spket IDE)
Select and install all of them

![](http://i.imgur.com/1flOAlB.png)


4) In Aptana Studio go to Windows -> Preferences -> Spket -> Javascript Profiles or Aptana Studio 3 > Preferences > Javascript Profiles Spket for mac.

5) Click "New" and write "SenchaTouch"

![](http://i.imgur.com/X3maNwa.png)

6) Select "SenchaTouch" and click "Add Library" and select "ExtJs" from the list displayed

7) Select "ExtJs" and click "Add File"

![](http://i.imgur.com/F0eslTU.png)

8) Locate youre "sencha-touch.jsb3" wich is containted in the zip file downloaded from sencha.com. (make sure all the files from that archive are located in the same folder)
.and click "Open"

![](http://i.imgur.com/7XEZ5tr.png)

![](http://i.imgur.com/R5CCX3f.png)

9) Select "SenchaTouch" again and click "Default" button

![](http://i.imgur.com/Ug8vrpV.png)

10) Click "OK"

Now open a ".js" script of a sencha touch project and check it out.

![](http://i.imgur.com/Yrpd1xz.png)
