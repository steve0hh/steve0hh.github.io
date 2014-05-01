---
layout: post
comments: true
---
Today I am gonna teach you guys how to create dropbox sync with this free text-expansion application [x-Type](http://www.adnx.com/i/apps/xtype4mac).

x-Type download link : [here](http://itunes.apple.com/us/app/xtype/id418108504?mt=12)

The only problem with x-Type is that there is no sync between computers. And people like us, with multiple computers will find it a hassel when we edit our snippets and not find the changes on the next computer. But fear not! [Dropbox](https://www.dropbox.com/) is here to save the day! :>

###How to do it :

Normally I like to create a folder in my dropbox. Hence my x-Type settings will go inside Dropbox > ApplicationSettings > x-Type (you can create your own type of folder structure, it doesn't matter)

![image](https://img.skitch.com/20120708-8en6f8m9jaerdbsr89jdiq4dd4.jpg)

1. Close x-Type application (Justi n case to prevent any errors)
2. Launch terminal application (click spotlight and type `terminal`)
3. Type:

        `cd ~/Library/Preferences`
4. As x-Type stores their application settings to this file: `com.app4mac.presto.plist`. We've to move x-Type application settings to my dropbox folder I type :

        `mv com.app4mac.presto.plist ~/Dropbox/ApplicationSettings/xType`

        (Users that are not familiar or fear the terminal too much just type `open .` terminal will open up finder and you manually move the file `com.app4mac.presto.plist` to your dropbox folder where it'll sync)

![image](https://img.skitch.com/20120708-mqu77aiqftiebuwj3td82b21t9.jpg)

5. Now we'll have to soft link the moved file in dropbox folder to the folder in the preferences. We do it with this command :

        `ln -s ~/Dropbox/ApplicationSettings/xType/com.app4mac.presto.plist com.app4mac.presto.plist`

![image](https://img.skitch.com/20120708-e6ms54pp1yasj7pj6g6k41yq9f.jpg)

6. Launch x-Type! it's as simple as that! :p

###On other Macs that you need to sync with
1. Launch terminal application (click spotlight and type `terminal`)
2. Type: 

        `cd ~/Library/Preferences`
3. Remove type(to remove the default settings):

        `rm com.app4mac.presto.plist`
4. Then soft link it to the `.plist` in your dropbox folder type:

        `ln -s ~/Dropbox/ApplicationSettings/xType/com.app4mac.presto.plist com.app4mac.presto.plist`

Feel free to comment on this post and I'll edit it accordingly! :)

## Update - Monday, 4 November, 2013
I've switched to [atext](http://www.trankynam.com/atext/) (I am in no ways affliated to the developer)

I feel it's just easier to use an app that has default syncing. :)
