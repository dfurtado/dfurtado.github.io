---
layout: post
title: "Using vim for development and how to make it awesome - part 3"
date:  2016-01-25 01:19:00 +0100
categories: development
description: "Third post of the series talking about vim enhancements"
---

Welcome to the part 3 of a serie of posts where I talk about how to make of vim editor awesome for development.

In the first part I talked about why I still using vim, its advantages and how to configure the NeoBundle, which
allows us to manage plugins easier. You can read the first part [here](/posts/vim-for-development/)

Part 2 I talk about how to install and setup Airline to enhance your tab and status bars. If you have missed you can also
read about it [here](/posts/vim-for-development-part2/)

In this post we will be talking about another awesome and useful plugin for vim called NerdTree. It will allow us to
visualize a folder structure that you are currently on, this way you can easily open files, navigate folder structures and so on.

Again, the installation is very straight forward with NeoBundle. You just need to edit your `.vimrc` and add these lines:

{% highlight bash %}

NeoBundle 'scrooloose/nerdtree'

{% endhighlight %}

Restart the vim and complete the installation.

When it's installed you can use the command `:NERDTreeToggle` to toggle the nerdtree.

**Tip:** It's possible to define custom shortkeys, for the NERDTree, personally I like mapping it to `ctrl+n`.
To do that, add `map <C-n> :NERDTreeTabsToggle<CR>` to your `.vimrc`

Toggle the NERDTree and you should see something like this:

![nerdtree](/assets/image/20160125/nerdtree.png)

Here's some of my favorite nerdtree features

1. File filters that can be toggle at runtime.
2. Show different of file types with different highlight.
3. Integrate very well with Airline.
4. Highly customizable.
5. Has mouse support **if you like mouse** :smirk:

Great!!! So now the Nerdtree is installed and working great however wouldn't be nice if there was some integration with
git so we could see what files have been added, changed, renamed, deleted an so on?
The good news is that there's a plugin for it and it's called `nerdtree-git-plugin`, so let's install it!!!!

The installation process is the same as the other plugins, add the line below to your `.vimrc` file.

{% highlight bash %}

NeoBundle 'Xuyuanp/nerdtree-git-plugin'

{% endhighlight %}

And we should also add this to our `.vimrc`

{% highlight bash %}

let g:NERDTreeIndicatorMapCustom = {
    \ "Modified"  : "✹",
    \ "Staged"    : "✚",
    \ "Untracked" : "✭",
    \ "Renamed"   : "➜",
    \ "Unmerged"  : "═",
    \ "Deleted"   : "✖",
    \ "Dirty"     : "✗",
    \ "Clean"     : "✔︎",
    \ "Unknown"   : "?"
    \ }
{% endhighlight %}

Restart vim and answer yes when asked if you wanna install the nerdtree-git-plugin and when it is finished toggle the
nerdtree with `ctrl+n` and if you are currently into a repo you should see the new symbols in front of the file names
indicating its state.

![nerdtree](/assets/image/20160125/nerdtree-git.png)

Lastly there's one more plugin that I would like to mention and it might be a good idea to install as well, the plugin is
called **vim-nerdtree-tabs**. The idea of this plugin is to add more functionality to nerdtree and make it look and feel more
like a panel.

When you install the nerdtree and start open several tabs, you will notice that the tab panel get labeled as **NERD_tree_1**
, the command `:NERDTreeTabsToggle` toggle the nerdtree in all opened tabs and my favorite feature, when you close a tab
there won't be any nerdtree panel open.

You can install it the same way as the NERDTree, with NeoBundle:

{% highlight bash %}
NeoBundle 'jistr/vim-nerdtree-tabs'
{% endhighlight %}

And then from now on instead of running `:NERDTreeToggle` use `:NERDTreeTabsToggle` :+1:

Now we have come to the end of one more post of the series about how to make your vim editor awesome for development.

Next up I will talk about tmux and how tmux integrate with all the other plugins that we have previouly installed.

### Useful links

1. Nerdtree :octocat: [https://github.com/scrooloose/nerdtree](https://github.com/scrooloose/nerdtree)
2. Nerdtree-git-plugin :octocat: [https://github.com/Xuyuanp/nerdtree-git-plugin](https://github.com/Xuyuanp/nerdtree-git-plugin)
3. Vim-Nerdtree-tabs :octocat: [https://github.com/jistr/vim-nerdtree-tabs](https://github.com/jistr/vim-nerdtree-tabs)

