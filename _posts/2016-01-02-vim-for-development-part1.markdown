---
layout: post
title: "Using vim for development and how to make it awesome - part 1"
date:  2016-01-02 15:10:00 +0100
categories: development
description: "Why I rather use vim than a IDE and how to make or vim awesome - part 1"
---

I started my career in computer science early 1997 and after a breaf time working developing DOS and Windows applications
I've got a job working in a bioinformatics laboratory and I switched over to UNIX platform more specificaly UNIX True 64.
At that time UNIX developers had just a few options to write their code but the most popular text editors were Pico (a couple
of years later GNU release Nano, which was a open source version of Pico), vi and Emacs.

Pico was great, it was simple to use and learn the commands, the interface was very similiar to the mail client Pine and it was a good
entry point for me since I was used with the Borland Turbo C and both of them were a bit more user-friendly editors. The only problem
was that Pico was inferior when compared with vi and Emacs and that made me quickly make the transition to Emacs.

Between 1998 and 2007 I've been using Emacs for development and even thou I was an Emacs kind of guy I also used vi on a daily
basis. In machine without Emacs, vi was always pretty handy when doing administration tasks, editing config files and writing scripts.

Since that time I am still using vi and I actually tried other text editors like Sublime, Atom and most rencently the Visual Studio code
and they are all pretty good (don't get me wrong) however I always go back to vi for its simplicity and speed, it feels more natural to me.

I decide to write this post after a discussion about it it still worth using vi for development since we have great text editors
like the aforementioned Sublime, Atom, Visual Studio Code, TextMate and others, plus all the IDEs available.

My answer to this question was **YES!** and here are some of the reasons:

1. Easy to use and fast.
2. Sometimes IDEs are more in the way than helping.
3. It's pre-installed on Macs and it comes with every Linux distro you can think of, plus many UNIX flavours.
4. Highly customizable.
5. Great community developing awesome plugins.
6. Vim is open source, you can check the project's page at [https://github.com/vim/vim](https://github.com/vim/vim)
7. Together with some plugins and tmux you are as productive if not more productive if you would ne using an IDE.
8. When starting to learn a new programming language I find much better to use a text editor than a IDE with all help and auto-complete features.

With that said I'm planning to write a serie of 4 posts:

* part 1 - Installing vim and NeoBundle.
* part 2 - Airline plugin and powerline fonts.
* part 3 - Nerd tree.
* part 4 - Tmux

By the end of this series you will have a development environment looking like this:

<img src="/assets/image/20160102/vim.png" width="680" height="425"/>

As you can see I'm using nerd tree plugin so I can easily browse the directory structure of my project and the airline plugin
so I get that nice tab bar on the top and the status line. My terminal is also splited into 3 panels one running vim on the top,
the one on the bottom left is running a gulp task and finally the one on the right is a terminal so I can run commands still having 
my vim visible. The vim theme I'm using here is called `maui`. 

So let's get started!

### First things first
If you don't have vim installed, you can run the command:

{% highlight bash %}
$ sudo apt-get update
$ sudo apt-get install vim
{% endhighlight %}

Some people prefer using Neovim which contains a few improvements over vim, if you want to test it out you can see how to install
[here](https://github.com/neovim/neovim/wiki/Installing-Neovim), however this post I will be covering vim.


### NeoBundle

NeoBundle is a very nice plugin manager for Vim based on Vundle plugin. NeoBundle make it very easy to manage our plugins, the
only thing you need to do is to run `:NeoBundle <repository name>`, it will search the plugin on GitHub repositories and download it
to the correct location for you. The repository name should be something like `'github_username/repo_name'`, to install
NeoBundle you can run the commands:

{% highlight bash %}
$ curl https://raw.githubusercontent.com/Shougo/neobundle.vim/master/bin/install.sh > install.sh
$ sh ./install.sh
{% endhighlight %}

After that you should be ready to go and now it's time to configure it. If you are compleatly new to Vim you want to
first create a `.vimrc` file on your home directory:

{% highlight bash %}
$ touch .vimrc
{% endhighlight %}

Alright! edit the .vimrc file and add the follwing code:

{% highlight vim %}
" Note: Skip initialization for vim-tiny or vim-small.
 if 0 | endif

 if has('vim_starting')
   if &compatible
     set nocompatible               " Be iMproved
   endif

   " Required:
   set runtimepath+=~/.vim/bundle/neobundle.vim/
 endif

 " Required:
 call neobundle#begin(expand('~/.vim/bundle/'))

 " Let NeoBundle manage NeoBundle
 " Required:
 NeoBundleFetch 'Shougo/neobundle.vim'

 " My Bundles here:
 " Refer to |:NeoBundle-examples|.
 " Note: You don't set neobundle setting in .gvimrc!

 call neobundle#end()

 " Required:
 filetype plugin indent on

 " If there are uninstalled bundles found on startup,
 " this will conveniently prompt you to install them.
 NeoBundleCheck
{% endhighlight %}

This settings were copied from the NeoBundle page on guthub for more information
check [https://github.com/Shougo/neobundle.vim](https://github.com/Shougo/neobundle.vim)

To install a bundle just start `vim` and run `:NeoBundleInstall`

That's all for now and next post we will talk about how to install the airline that will make your vim status bar and tab bar
looks awesome!
