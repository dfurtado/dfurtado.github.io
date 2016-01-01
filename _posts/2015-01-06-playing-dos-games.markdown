---
layout: post
title: "Playing DOS games on Linux" 
date:   2015-01-06 16:56:37 +0100
categories: javascript
description: "Post about how to setup up and play or favorite DOS game on Linux!"
---

If you’re like me (have been playing computer games in the 90’s) and really miss Doom, Doom 2, Price of Persia, 
Duke Nuken 3D and so many other classic DOS games, you will be happy to know that it’s possible to play those 
games on new hardware. Of course you could try to bring back to life that old machine that is laying around 
full of dust at your parent’s house, or you can use DOSBox. DOSBox is a MS-DOS emulator built with SDL which 
means you can run it in different platforms (Windows, Linux, Mac). The installation and configuration is pretty 
straight forward and the games run perfectly!

I’m currently running it on Linux on a Debian distribution and here are the steps to get it up and running:

First you want to update the repositories:

`sudo apt-get update`

Now we can run:

`sudo apt-get install dosbox`

To start simply type: `dosbox`

When it starts it’s time to mount the drive where your games are located, you can do that with the command:

`mount c /path_to_my_games/`

This command will mount the directory where you have your games as drive C.

Change over to C drive, execute the game and be happy! =D

Here’s Doom 2 running on my Debian

<img src="/assets/image/20150106/doom2.png">


