---
layout: post
comments: true
---

`Encoding::InvalidByteSequenceError` on Raspberry Pi SiriProxy server everytime Siri on iPhone runs.

**Error** :

Raspberry Pi SiriProxy server crashes showing `Encoding::InvalidByteSequenceError` at `/usr/local/rvm/gems/ruby-1.9.3-p385@SiriProxy/gems/CFPropertyList-2.2.0`
everytime Siri on your iPhone starts.

Error message as shown below :

![image](http://i.imgur.com/bxlhRHy.png)

**Solution** :

After reading [this article on the similar issue](https://github.com/plamoni/SiriProxy/issues/420), I've decided to try out [this issue comment](https://github.com/plamoni/SiriProxy/issues/420#issuecomment-12804053) as it seems the most reasonable.

Which is replacing the entire `CFPropertyList-2.2.0` folder with the contents of [CFPropertyList-2.1.2](http://rubyforge.org/frs/download.php/76604/CFPropertyList-2.1.2.zip)

1) Enter the containing folder of `CFPropertyList-2.2.0`

	cd /usr/local/rvm/gems/ruby-1.9.3-p385@SiriProxy/gems/
	
2) Copy `CFPropertyList-2.2.0` folder out in case we screw things up a little

	cp CFPropertyList-2.2.0 ~
	

3) Download the zip file (in Pi's terminal) :

	curl -O -L http://rubyforge.org/frs/download.php/76604/CFPropertyList-2.1.2.zip
	
4) Unzip the zip file and delete the zip

	unzip CFPropertyList-2.1.2.zip
	rm CFPropertyList-2.1.2.zip
	
After this, you should see a folder called `CFPropertyList-2.1.2` if you do the [`ls` command.](http://en.wikipedia.org/wiki/Ls)
	
5) Delete the original `CFPropertyList-2.2.0` folder

	rm -rf CFPropertyList-2.2.0
	
6) Rename the new `CFPropertyList-2.1.2` folder to `CFPropertyList-2.2.0`

	mv CFPropertyList-2.1.2 CFPropertyList-2.2.0
