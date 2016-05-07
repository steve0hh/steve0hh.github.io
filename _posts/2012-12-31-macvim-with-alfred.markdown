---
layout: post
comments: true
---

Today i'm going to talk about launching MacVim with alfred.

If you guys install MacVim through `brew` command, I guess you'll notice that alfred can't pick up MacVim.app as it wasn't installed in the /Applications directory.

I?ve try symlinking it to the Applications directory, but Alfred does not pick up .symlink files too.

Moving the MacVim.app file to /Applications folder is not recommended as it will render the ?mvim? command useless.

Now, there?s a tip which allows Alfred to launch it.

#### 1. Launch Alfred and press `CMD + ,`

#### 2. Go to Features > Default Results

#### 3. Under `Search Scope setting`, hit the + sign

![Image](http://i.imgur.com/7KwU8.png)

#### 4. Now search for the folder where MacVim is located in.

To find the folder where MacVim is located in, my recommended way is to launch terminal.
Normally it is located in

    usr/local/Cellar/macvim

So I would type something like

    open usr/local/Cellar/macvim

Then drag and drop the folder to the file browser like what is done in the following picture.

The file browser will automatically be in the containing folder that you have just dragged into.

![Image](http://i.imgur.com/av2DW.png)

#### 5. The last and final step is to add that folder to the Search Scope of Alfred.

There you go, now you can launch MacVim through Alfred.

Enjoy!

Regards,
Steve
