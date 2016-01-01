---
layout: post
title:  "Getting the Lenovo Thinkpad T400 Wifi adapter to work on Debian Jessie (and Wheezy)"
date:   2015-08-02 16:56:37 +0100
categories: linux
description: "Small post about setting up wifi on a lenovo T400 laptop on Linux"
---

The best thing of being a Linux user is that you have a reliable and robust system, a great community who helps each other and great developers working tirelessly to fix bugs and security holes fast but one of the things I most like about Linux is that it is a lightweight system. Because Linux is highly customizable you install only the things you actually need and that allows us to bring those old laptops and desktops back to life!!!

About 1 year ago I’ve got from an old employer one Lenovo Thinkpad 400 that was basically unusable for development (when Windows was installed on it). I have installed the Wheezy on it and it worked perfectly except the wifi adapter, after google a bit and asking people in the community I’ve got it to work!! I have a few friends that have the same laptop or other older thinkpads so I decided to go ahead and write how to get the wifi adapter to work. We will be covering Wheezy and Jessie.

To start things off we need to add the contrib and non-free components to /etc/apt/source.list

`# deb http://http.debian.net/debian/ jessie main contrib non-free`

If you are using Wheezy:

`# deb http://http.debian.net/debian/ wheezy main contrib non-free`

Then we update our package list:

`# apt-get update`

Now the kernel driver iwlwifi needs to be installed so the wifi adapter (Intel Corporation Ultimate N WiFi Link 5300) of the Lenovo Thinkpad T400 works properly, to do that run the command:

`# apt-get install firmware-iwlwifi`

Lastly, we need to make it permanent so the iwlwifi module will be loaded at the startup, we can do that using the command modprobe:

`# modprobe -r iwlwifi; modprobe iwlwifi`

Now your Lenovo Thinkpad T400 should be good to go :)
