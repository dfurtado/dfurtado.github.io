---
layout: post
title:  "MSBuild tools version in npm"
date:   2015-08-05 16:56:37 +0100
categories: msbuild
description: "Just a short post about a very handy option in npm which allow us to specify the msbuild version we are using."
---
Just a little trick I’ve learned today!

I’m currently doing a training called MongoDB for NodeJS developers and when I tried to install the mongoDB driver I’ve got a little surprise:

{% highlight console %}
C:\Users\daniel\node_modules\mongodb\node_modules\mongodb-core\node_modules\kerberos
> node "C:\Program Files\nodejs\node_modules\npm\bin\node-gyp-bin\\..\..\node_modules\node-gyp\bin\node-gyp.js" rebuild
Building the projects in this solution one at a time. To enable parallel build, please add the "/m" switch.
C:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140\Microsoft.Cpp.Platform.targets(55,5): error MSB8020: The build tools for Visual Studio 2010 ( Platform Toolset = 'v100') cannot be found. To build using the v100 build tools, please install Visual Studio 2010 build tools.  Alternatively, you
may upgrade to the current Visual Studio tools by selecting the Project menu or right-click the solution, and then selecting "Retarget solution". [C :\Users\daniel\node_modules\mongodb\node_modules\mongodb-core\node_modules\kerberos\build\kerberos.vcxproj]
mongodb@2.0.39 ..\..\..\..\node_modules\mongodb
├── readable-stream@1.0.31 (string_decoder@0.10.31, isarray@0.0.1, inherits@2.0.1, core-util-is@1.0.1)
├── es6-promise@2.1.1
└── mongodb-core@1.2.6 (bson@0.4.8, kerberos@0.0.12)
{% endhighlight %}

After some research I’ve found out that the mongodb package targets the VS msbuild tools 2010 and I don’t have that installed and to get to work I would use the msvs_version key in the npm command, something along these lines:

`npm install mongodb --save-dev --msvs_version=2015`

After that everything worked just fine and I managed to install the mongoDB driver.
