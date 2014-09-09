---
layout: post
comments: true
---

Helloworld!

Recently I just came across this command-line todo manager called [Taskwarrior](http://taskwarrior.org/).

Everything was working fine until I tried to [sync my task lists](http://freecinc.com/) via the command `task sync init`, I got this error:

    Taskwarrior was built without GnuTLS support.  Sync is not available.

This was because I installed it via [homebrew](http://brew.sh/) and did not install one of their dependencies installed.

Well.. Luckily for me, it's one easy error to solve.

To install GnuTLS via homebrew, just run:

    brew install gnutls

After that, just run

    brew uninstall task

then re-install it:

    brew install task

After that, syncing should work for you.

Just like mine.:)

![successful syncing](http://i.imgur.com/7fWKbF1.png)
