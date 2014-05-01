---
layout: post
comments: true
---

So this is yet another vimperator tip! :)

So I encountered this issue where I wanted to add another search engine to vimperator.

![vimperator search](http://i.imgur.com/L8CC09c.png)

So I thought to myself.. There must be an easier way right?

THIS IS VIMPERATOR!!!

![spartan](http://i.imgur.com/160quGD.jpg)

Google searched around the internet.. Didn't found a decent guide....
But I actually followed this [post](https://support.mozilla.org/en-US/questions/780073) and did some trial and error for it.

So here's it! :D

But before that, search [Mycroft Project](http://mycroftproject.com/) to see if they already have the search engine plugin that you have. If they do not have it. Follow the guide below to create one! :)

1) Find the website that you want the custom search engine in. For example, I wanted to add [namecheap](https://www.namecheap.com/)

2) Go search some useless stuff! :)

![useless namecheap search](http://i.imgur.com/TjAcANm.png)

3) See the URL, normally it'll be a GET request.
So mine was `https://www.namecheap.com/domains/registration/results.aspx?domain=helloworld`.

4) Analyse

So for [namecheap](https://www.namecheap.com/)
https://www.namecheap.com/domains/registration/results.aspx?domain=**helloworld** is the same as my search term!

![namecheap url](http://i.imgur.com/ENTuCoQ.png)

5) Go to [Mycroft Project page](http://mycroftproject.com/)
In side side bar, hit "Create/Submit Plugin"

![mycroft side nav bar](http://i.imgur.com/WqX23us.png)

Scroll down and you'll be greeted with this form.

![create plugin form](http://i.imgur.com/JpnnobSl.png)

6) Fill it up! The only thing you've to take note of is the "Search URL" field.

So you'll have to edit your search term in your url to `{searchTerms}`.(Note that it's case sensitive)

For example, my original url is

    https://www.namecheap.com/domains/registration/results.aspx?domain=helloworld

My input at the "Search URL" field will be

    https://www.namecheap.com/domains/registration/results.aspx?domain={searchTerms}

7) Generate plugin and Firefox will ask if you would like to add a search engine..
Just follow the on screen instructions and you'll be done! :)

Do comment in this post if you found any mistakes and I'll edit it accordingly. :)
