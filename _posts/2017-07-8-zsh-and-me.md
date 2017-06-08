---
title : "She sells seashells by the Z shell"
image : /assets/image/zsh-hero.png
layout : post
excerpt : "An introduction to making your terminal beautiful and easy cos well, we use the terminal a lot"
tags : 
    - terminal
    - linux 
    - tutorial
---
Now we all know the power of bash. 

It's scary but once you get to understand it you love it(At least in my case). It arguably makes work faster though the GUI guys may argue otherwise. So I was checking out a video tutorial online and I saw the instructor using a really beautiful shell, like so beautiful. Well he said "For all those wondering I am using Zsh"...
Whooaa, now there goes me, straight to Google to search Zsh. I spent my free time reading about [Zsh](https://en.wikipedia.org/wiki/Z_shell), why I would want to use Zsh and Oh my God(Zsh), those lovely themes!. Realized I could change themes and add plugins with a framework called [Oh-my-zsh](https://ohmyz.sh/). 

Check out some themes : 

#### [Agnoster](https://github.com/agnoster/agnoster-zsh-theme)
![Agnoster](/assets/image/agnoster-zsh.png)

#### [YS](http://blog.ysmood.org/my-ys-terminal-theme/)
![YS](/assets/image/ys-zsh.png)

#### [Pure](https://github.com/sindresorhus/pure)
![Pure](/assets/image/pure-zsh.png)

So let's begin. I am on Linux so sadly I will only be able to provide a linux tutorial.
First you install zsh from your distro's repos. If you are on Ubuntu, Debian or all the debian derivatives you can simply install by banging in this command

> sudo apt install zsh

If you are on Arch or Manjaro(I use Manjaro), you can simply install from the Arch User Repositories.

Once you are done installing Zsh, you can have a peek at it by simply typing in Zsh in your terminal. That should take you into Zsh. But hey, you want Zsh as default right? 

To make Zsh the default shell, bang in this command : 

>sudo chsh -s $(which zsh)

This should make Zsh your default shell. You may have to re-login for the new setting to apply






