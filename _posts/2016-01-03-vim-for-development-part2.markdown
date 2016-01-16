---
layout: post
title: "Using vim for development and how to make it awesome - part 2"
date:  2016-01-03 01:19:00 +0100
categories: development
description: "Second part of my tutorial about how to make your vim looks awesome!"
---

Here's the part 2 of my series of posts talking about how to make the vim editor nice for development.

If you didn't read the first part, I covered how to install the NeoBundle which is a package manager for vim. I strongly
recomend read the first part if you are not familiar with NeoBundle. Click [here](/posts/vim-for-development/) to read.

### Vim-Airline

Airline is a vim plugin that will enhance your vim tab and status bar. The airline plugin is highly customizable you can change
basically everything you need. You can change what information will be displayed, theme and integrates pretty well with lots of
other plugins.

The installation is very simple all you need to do is to edit your `.vimrc` file and add `NeoBundle 'bling/vim-airline'` right
above the `call neobundle#end()` and restart vim. When the vim is restated NeoBundle will ask if you want to install the new
plugin, it's only the answer yes and you should be ready to go.

After that the only thing we need to do is add some configuration to our `.vimrc`

{% highlight vim %}
set noshowmode
set noruler
set laststatus=2

let g:airline_powerline_fonts=1
let g:airline#extensions#tabline#enabled = 1
let g:airline_theme = 'luna'
{% endhighlight %}

This can be added in the end of your `.vimrc`

Just a short explanation of what those seetings do:

`set noshowmode` will disable showing vim's current mode in the vim's status bar since we will be displaying it on
the airline tab we disable it so it's not displayed twice.

`set norule` hides the ruler. The ruler shows information about the which line and column the cursor is current at. We disable
it so it is only displayed in the airline status bar.

`set laststatus=2` will tell vim to always display the status bar, so the airline status bar is always visible.

`let g:airline_powerline_fonts=1` will enable to poweline fonts. It will give a nicer look and feel to the status bar.

`let g:airline#extensions#tabline#enabled = 1` enable the the smart tab which will display all the buffers when there's only
one tab open.

Finally `let g:airline_theme = 'luna'` sets the airline theme. I'm using luna but you can change for any theme you like
you can get a list of the available themes [here](https://github.com/bling/vim-airline/wiki/Screenshots).

Since we enabled powerline fonts, we need to install them. To do that is pretty straight forward.

{% highlight bash %}
git clone https://github.com/powerline/fonts.git
cd fonts && ./install.sh
{% endhighlight %}

The fonts will be installed at `$HOME/.local/share/fonts`

Lastly we need to make sure that the terminal is configure to use 256 colors a very detailed instruction on how to do it
can be found [here](http://vim.wikia.com/wiki/256_colors_in_vim)

That's all for now folks, next post we will install a very useful plugin the NerdTree.




