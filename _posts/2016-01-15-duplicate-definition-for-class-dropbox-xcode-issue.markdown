---
layout: post
comments: true
---

Hi guys,

Recently, I’ve been doing some iOS programming during my free time and found out about the following error that I think is pretty frustrating for people.

Problem:
I am using xcode and cocoapods to setup a project.
Installed parse as a dependency in cocoapods.
Everything was working fine on my iMac, then I used dropbox to sync code between 2 computers.

Sidenote: I prefer using my iMac to do development at home and I use my Macbook air to do development at school. I don’t like to use git to sync my code as I think it’ll dirty my commit history and I don’t like the idea to do a `git push —force` to rewrite history. Hence I am using dropbox to sync the code. I still use git to version control my code. :)

Now I have another Macbook air which I use in school but when I tried to build the project using the macbook air, it shows the following error:

```
Duplicate interface definition for class 'BFAppLink'
```

But on my iMac, without doing anything, it is still building without any errors.

After googling around EXTENSIVELY.. (I copy and pasted my error as a whole.. stupid me.. )
I found out about this question on stackoverflow which is basically my problem! :D

[http://stackoverflow.com/q/27829203/765960](http://stackoverflow.com/q/27829203/765960)

There is [awesome answer](http://stackoverflow.com/a/29102808/765960) provided by user `Billy Lavoie` :

Now, for you guys that don’t know how to do selective sync on dropbox please follow the following steps:

### 1. Select the dropbox icon
![screen_shot_2016-01-15_at_5_00_51_pm](https://cloud.githubusercontent.com/assets/682923/12355294/9e3893e4-bbd6-11e5-86e2-04f4aed05491.png)

### 2. Go to dropbox preference:
  1. Click the gear icon
  2. A dropdown should appear
  3. Click on preference (A popup should appear)

![screen_shot_2016-01-15_at_5_01_19_pm](https://cloud.githubusercontent.com/assets/682923/12355311/b73e5a5e-bbd6-11e5-876b-fdbe00368b88.png)


### 3. Selective sync
  1. Click on “account”
  2. Click on “selective sync”

![screen_shot_2016-01-15_at_5_01_36_pm](https://cloud.githubusercontent.com/assets/682923/12355318/c53ce332-bbd6-11e5-9b02-cc5328ec6509.png)

### 4. Find your project folder
  1. Inside the project folder, you should find /Pod/Header inside it
  2. Uncheck it

![15_1_16__10_26_pm](https://cloud.githubusercontent.com/assets/682923/12355383/3531c162-bbd7-11e5-9687-5e0573fcb9bf.png)


### 5. Open your terminal, go to your project folder do `pod install`

Note: you should only need to run pod install once to set up each of the computer that you are developing on once or when you add new dependencies. :)

Hope that helps. :)

Steve
