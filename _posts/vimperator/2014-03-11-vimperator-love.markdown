---
layout: post
comments: true
---

Yes, I am a huge fan of vimium for chrome previously which resulted in the [previous tips for chrome](http://steve0hh.wordpress.com/2013/05/11/chrome-losing-focus-on-webpage/).

But last week, I've tried vimperator and totally fell in love with it! :)
Vimium is nice, but not as powerful as vimperator!

![vimperator rocks!](http://i.imgur.com/MeFT1ak.jpg)

This is the only reason I'm using Firefox. :D

## Tips and trick

Vimperator, like vim, uses a RC file to load user's customization. The file vimperator uses is `~/.vimperatorrc`.

Things I like to do so far.

### Make j/k scrolling scroll more

    :noremap j 3j
    :noremap k 3k

### Map J/K tab left and right respectively

    :noremap J gT
    :noremap K gt


**and lastly**


As vimperator uses so many key bindings, mostly, useful extensions like [pinterest](http://www.pinterest.com/), [delicious](https://delicious.com/) and [readability](https://www.readability.com/)'s key binding will fail. **But** worry not! :)

Because popular sites like that, often provide bookmarklets for people that do not want to install their extensions.


Vimperator is **AWESOME!!**

### Add our own bookmarklets!

    command! -nargs=0 -description="description you want ot put" commandthatyouwant open yourjavascriptcommand

So for example, I would like to have readability's readnow function, the steps I would take are:

1) Head over to [readability's bookmarklet page](https://www.readability.com/bookmarklets)

2) Right click on the "Read now" button and click "Copy Link Location"

![readnow](http://i.imgur.com/d6hNSpM.png)

3) Create your bookmarklet!

    command! -nargs=0 -description="Read now with readability" readnow open javascript:(%0A%28function%28%29%7Bwindow.baseUrl%3D%27//www.readability.com%27%3Bwindow.readabilityToken%3D%27%27%3Bvar%20s%3Ddocument.createElement%28%27script%27%29%3Bs.setAttribute%28%27type%27%2C%27text/javascript%27%29%3Bs.setAttribute%28%27charset%27%2C%27UTF-8%27%29%3Bs.setAttribute%28%27src%27%2CbaseUrl%2B%27/bookmarklet/read.js%27%29%3Bdocument.documentElement.appendChild%28s%29%3B%7D%29%28%29)

4) Now, go to firefox and hit `;` and type `readnow` then ENTER.

5) Profit! :)
