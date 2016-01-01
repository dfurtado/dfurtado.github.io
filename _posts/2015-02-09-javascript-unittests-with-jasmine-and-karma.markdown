---
layout: post
title:  "JavaScript Unit tests with Jasmine and Karma"
date:   2015-02-09 16:56:37 +0100
categories: javascript
description: "A step-by-step guide on how to setup karma and write unit test for your JavaScript code wuing Jasmine"
---

It’s not any news that JavaScript is a big deal nowadays. Back in the day JavaScript was basically synonymous of web development but today it is not limited for web development. Front-end, back-end, games, mobile applications and much more is developed in JavaScript and because of that it is more important than ever to write maintainable and testable code.

Recently I’ve been doing some research, evaluating different frameworks and test runners and I was blown away by the combo Jasmine and Karma.

The intention of this post is the help you get started and not to show the ins and outs of Jasmine and Karma.

So let’s get started!!!

To start let’s create the folder structure of our project:

{% highlight bash %}
~$ mkdir jsunittest
~$ cd jsunittest/
~/jsunittest$ mkdir scripts
~/jsunittest$ mkdir tests
{% endhighlight %}

we are going to create a small class with some math utility functions. I’m writing all the code in Typescript but it can be written as vanilla JavaScript, Coffee script, it’s your choice, no parents no rules! ;D

On the scripts folder create a file called MathUtils.ts and add the code bellow:

{% highlight javascript %}
module Libs {
 
	export class MathUtils {
 
		public fibonacci(n:number): number {
 
			if(n < 0) throw "Invalid number";
 
			if (n === 0) return 0;
			if (n === 1) return 1;
 
			return this.fibonacci(n - 1) + this.fibonacci(n - 2);
		}
 
		public isPrime(n:number): boolean {
 
			if(n === 1 || n === 2) return false;
 
			for(var i = 2; i < n; i++) {
				if(n % i === 0) return false;
			}
 
			return true;
		}
 
	}
 
}
{% endhighlight %}

Alright, now we have the class we are going to test but before that lets install everything we need to write and execute our tests.

First we are going to install the karma test runner:

{% highlight bash %}
~/jsunittest$ npm install karma --save-dev
~/jsunittest$ npm install karma-jasmine --save-dev
{% endhighlight %}

To make things easier for us lets also install karma client globally

{% highlight bash %}
~/jsunittest$ npm install -g karma-cli
{% endhighlight %}

The nice thing about Karma is that you can run the test in multiple browsers, that is possible through the launchers. You can install as many launchers as you want but for now I’m going to install only the PhantomJS launcher, if you’re not familiar with PhantomJS you can read more about it (here)[http://phantomjs.org].

{% highlight bash %}
~/jsunittest$ npm install karma-phantomjs-launcher --save-dev
{% endhighlight %}

We are all set to start creating our tests, create a file called MathUtilsTest.ts in the tests folder and add the code bellow:

{% highlight javascript %}
describe("Mathutils test", () => {
 
	var _mutils = new Libs.MathUtils();
 
	it("Should return true when passing a prime number", () => {
	
		expect(_mutils.isPrime(3)).toBe(true);
 
	});
 
	it("Should return false when passing a non-prime number", () => {
		
		expect(_mutils.isPrime(1)).toBe(false);
	
	});
 
	it("Should return the 10th number on a fibonacci sequence", () => {
 
		expect(_mutils.fibonacci(10)).toBe(55)
	
	});
 
	it("Should throw exception when passing negative values", () => {
	
		expect(() => _mutils.fibonacci(-1)).toThrow();
	
	});
 
});
{% endhighlight %}

Now the only thing that is left is to create a Karma config file and run our tests.

Karma creates the file for you, the only thing you need to do it run **karma init** and answer the questions:

{% highlight bash %}
~/jsunittest$ karma init
 
Which testing framework do you want to use ?
Press tab to list possible options. Enter to move to the next question.
> jasmine
 
Do you want to use Require.js ?
This will add Require.js plugin.
Press tab to list possible options. Enter to move to the next question.
> no
 
Do you want to capture any browsers automatically ?
Press tab to list possible options. Enter empty string to move to the next question.
> PhantomJS
> 
 
What is the location of your source and test files ?
You can use glob patterns, eg. "js/*.js" or "test/**/*Spec.js".
Enter empty string to move to the next question.
> tests/*.js
> 
 
Should any of the files included by the previous patterns be excluded ?
You can use glob patterns, eg. "**/*.swp".
Enter empty string to move to the next question.
> 
 
Do you want Karma to watch all the files and run the tests on change ?
Press tab to list possible options.
> no
 
 
Config file generated at "/home/daniel/jsunittest/karma.conf.js".
{% endhighlight %}

There’s one last thing we need to do, in order to run the tests we will need to add every dependency we have in our tests so these files are also loaded when running the tests, in this case our tests have one dependency, the file MathUtils.js (after the compilation is .js and not .ts), so let’s go ahead edit the karma config file and add this dependency in the files array. To make things easier, just all JS files in the script folder:

{% highlight javascript %}
// list of files / patterns to load in the browser
files: [
   'scripts/*.js',
   'tests/*.js'
],
{% endhighlight %}

Finally we can run the tests:

{% highlight bash %}
~/jsunittest$ karma start
INFO [karma]: Karma v0.12.31 server started at http://localhost:9876/
INFO [launcher]: Starting browser PhantomJS
INFO [PhantomJS 1.9.8 (Linux)]: Connected on socket 1pGN800gAYbryv2R73cs with id 63370353
PhantomJS 1.9.8 (Linux): Executed 4 of 4 SUCCESS (0.003 secs / 0.002 secs)
{% endhighlight %}

In the output you can see that it ran all 4 tests using the PhantomJS launcher. All tests passed with great success!! =D


### But WAIT!!! That’s not all I have to talk about! =D

## Karma file watcher

When we are working on the tests would be useful the tests run every time changes in the files are saved. Notice that during the Karma configuration we answered that we don’t want Karma to watch for file changes. To change this setting is simple, edit the Karma config file and change, the option singleRun to false:

{% highlight javascript %}
// Continuous Integration mode
// if true, Karma captures browsers, runs the tests and exits
singleRun: false
{% endhighlight %}

Now when you run karma start again, Karma will be watch any changes on your tests and soon as you save those changes Karma will run the tests again.

## Generating test results reports

Karma also has loads of plugins for report creation, that is specially useful when running the tests in a continuous integration environment. On this post I will use the karma-html-reporter. When using the karma-html-reporter every time you run the tests it will be generated a HTML page containing the tests results. To install you can simple do:

`npm install karma-htmlfile-reporter --save-dev`

You have two options to generate the HTML report, the easiest is to add “report” to the reporters property in the Karma configuration:

{% highlight javascript %}
reporters: ['progress','html'],
{% endhighlight %}

Then you can just go ahead and run **karma start** and you should see a file called results.html that looks like this:

There’s also a option to set the reporter to use in the command-line like this:

`~/jsunittest$ karma start --reporters dots,html`

## Useful links

Karma: [https://karma-runner.github.io/0.12/index.html](https://karma-runner.github.io/0.12/index.html)

Jasmine: [https://jasmine.github.io/](https://jasmine.github.io/)

Typescript: [http://www.typescriptlang.org/](http://www.typescriptlang.org/)


Hope you all liked this post and let me know what you think about Karma, jasmine or if you use another test framework. I would love to hear your opinions.

Happy coding!








