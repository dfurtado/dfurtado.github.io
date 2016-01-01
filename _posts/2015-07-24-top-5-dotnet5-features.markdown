---
layout: post
title:  "Top 5 .NET 5 features"
date:   2015-07-25 16:56:37 +0100
categories: development
description: "My favorite features on .NET 5"
---

Couldn’t let be and do a top 5 asp.net 5 features, so let’s dive into it!

### 1. Cross-platform

I think that’s something that everyone in the .NET community is most excited about. Sure, we have had project 
mono before but unfortunately I haven’t seen so much mono projects in production environments. When Microsoft 
takes this step I’m sure there will be lots of developers adopting .NET in their projects. Thumbs up!!!

Now I’m waiting Visual Studio for Linux and Mac. :)

### 2. Dependency injection out of the box

Don’t get me wrong, I love Autofac and Ninject and I have been using both of them in various projects however 
I like to keep my applications with less 3rd party dependencies as possible. I never understood why it took 
so long for the .NET team add this feature. A very simplistic implementation of a DI Container will be provided 
and can be used out of the box if your project doesn’t require complex injection capabilities.

The framework provides an abstraction (IServiceProvider interface) which can be used to replace the default 
implementation with our own container and all the framework components like MVC, Web API, Entity Framework, 
SignalR rely on the capabilities of IServiceProvider.

### 3. Cloud optimized runtime.

The Core CLR have been re-designed into modules which means that your application will have the flexibility 
of adding only the necessary features.

It is possible to have multiple applications running on different framework version. Allowing side by side 
execution/self-container per application will

### 4. Tag Helpers

This is also a really nice feature. I kind of like the razor syntax and I use the html helpers a lot but 
wouldn’t it be great if the markup would look more like standard HTML and we didn’t need to have so much 
C# and HTML code living on the same file?

For example, in a razor view you can have the following link:

{% highlight html %}
@Html.ActionLink("My Link", "FooAction", "FooController", null, new { @class = "foo-css-class" })
{% endhighlight %}

With the tag helpers would look like this:

{% highlight html %}
<a controller="FooController" action="FooAction" class="foo-css-class">My Link</a>
{% endhighlight %}

It just looks nicer, cleaner and the CSS coders in our team will thank you for writing markup like this. :)

### 5. Open-source

ASP.NET is now open-source!!! For me this is the highest point of this release, for a long time Microsoft walked against the wind, ignoring the importance of open-source software and now ASP.NET is finally open-source. I’m really happy with this initiative, now we can run .NET apps in different platforms, Visual Studio 2015 has support for open-source tools like grunt, bower and gulp. It’s awesome to see the new Microsoft listening to the development community.

There’re much more really nice things that I didn’t talk about for example, improvements in the ASP.NET routing system, Assembly Neutral Interfaces and Dependency Resolution.

It’s a good time to be a .NET developer!


