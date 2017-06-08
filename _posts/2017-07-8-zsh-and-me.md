---
title : "She sells seashells by the Z shell"
image : /assets/image/seashell-cover.jpg
layout : post
excerpt : "An introduction to making your terminal beautiful and easy cos well, we use the terminal a lot"
tags : 
    - terminal
    - linux 
    - tutorial
---
Now we all know about the power of bash. 

It's scary but once you get to understand it you love it (At least in my case). It arguably makes work faster though the GUI guys may argue otherwise. So I was checking out a video tutorial online and I saw the instructor using a really beautiful shell, like so beautiful. Well he said "For all those wondering I am using Zsh..."
Whooaa, there goes me, straight to Google to search Zsh. I spent my free time reading about [Zsh](https://en.wikipedia.org/wiki/Z_shell), why I would want to use Zsh and Oh my God(Zsh), those lovely themes!. Realized I could change themes and add plugins with a framework called [Oh-my-zsh](https://ohmyz.sh/). 

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

If you are on Arch or Manjaro (I use Manjaro), you can simply install from the Arch User Repositories.

Once you are done installing Zsh, you can have a peek at it by simply typing in Zsh in your terminal. That should take you into Zsh. But hey, you want Zsh as default right? 

To make Zsh the default shell, bang in this command : 

>sudo chsh -s $(which zsh)

This should make Zsh your default shell. You may have to re-login for the new setting to apply

Now we have Zsh installed but it's still black and white and isn't lovely. We need to install oh-my-zsh for themes to work now.

To install, bang in this command : 

>sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"

Once it's done, close your terminal and open again, and you will be met with a configuration screen, follow the prompts closely till you are done. Now we have Oh-my-zsh installed but there are still no colors.

For colors, we need to install a plugin called [Zsh-Syntaz-Highlighting](https://github.com/zsh-users/zsh-syntax-highlighting/)

To install, use this command (Remember Arch users can just keep using the AUR to install these things) : 

> git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

There is a beautiful config file called '.zshrc' in your home folder. Remember it's hidden so just enable hidden files or folder in your file manager. You can do this by simply using the shortcut <kbd>Ctrl</kbd> + <kbd>H</kbd>

Open the zshrc file with your favorite text editor. Look for the plugins entry and add 'zsh-syntax-highlighting' to it. It should always be the last plugin in the array.

![zsh-syntax-highlighting](/assets/image/zshrc-plugins.png)

Save the file and reload, your colors may finally show up. 
You can browse this [link](https://github.com/robbyrussell/oh-my-zsh/wiki/themes) for themes to choose from. Once you find a nice theme from the list, you open the .zshrc file and edit the theme entry

![zshrc](/assets/image/zshrc.png)

Now you are done, you have a really beautiful terminal you can be proud anytime you open it. I will be talking about some interesting plugins and more customizations you can add to Zsh in my next post so stay tuned. Now go grab yourself some coffee or tea and enjoy your new shell.

Hey wait, check out my Zsh theme!. It's called lambda-mod
![zsh-hero](/assets/image/zsh-hero.png)
 





