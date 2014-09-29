---
layout: post
title: Reset your login credentials for "Visual Studio Tools for Git"
---

If you change your login credentials for one of the git hosting services (github, bitbucket, …) and you try to pull, fetch or push you probably receive the same error as in the screenshot below:

![](http://tobivnext.files.wordpress.com/2013/02/021313_1429_resetyourlo1.png?w=580)

I struggled a while with the problem until I found the solution.

**You have to reset the credentials in the Windows Credential store.**

> Sorry, I have to translate the text on the fly because I have a German version of Windows 7.

Go to your user account settings and click on “manager your own credentials”:

![](http://tobivnext.files.wordpress.com/2013/02/021313_1429_resetyourlo2.png?w=580)

Pick the credentials for e.g. git: [https://bitbucket.org](https://bitbucket.org) and click on edit:

![](http://tobivnext.files.wordpress.com/2013/02/021313_1429_resetyourlo3.png?w=580)

You should now be able to work with your git remote again:

![](http://tobivnext.files.wordpress.com/2013/02/021313_1429_resetyourlo4.png?w=580)

Hope this helps!
