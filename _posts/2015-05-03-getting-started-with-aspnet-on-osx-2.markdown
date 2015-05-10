---
layout: post
title:  "Getting Started with C# on OSX Part 2: Setting up the tooling"
date:   2015-05-03
date-day: 3rd
date-month: May
date-year: 2015
categories: C# ASPNET OSX
---

In [part one]() of the series, we took a look at the history of C# cross-platform development.

In this post, we're going to set up a development environment to get started coding.

(Note, for now this article will be addressing OSX only. I will update it to include Linux and Windows later.)

Pre-Requisites:

* A computer running OSX
* Basic programming ability
* How to google


After we're done, we will have the following applications installed:

* Git
* Homebrew - OSX Package Manager
* Mono - Open Source .Net implementation
* DNVM - The .Net Version Manager
* DNX - The .Net Execution Manager


So let's get started.
Open up your terminal, because we're going to be working in it for a little bit.

###Git###
Git is a version control management system.
You can grab it at their [site](http://git-scm.com/downloads)
We'll need to use git to grab some source code to make sure all of our shiny new tools are working as expected.

###Homebrew###
Homebrew is a package manager for OSX. It allows a clean way to install, update, remove, and manage software installed on your computer.
[Click here](http://brew.sh/) and follow the instructions to install it.

###Mono###
Mono is an open source implementation of the .Net execution environment. This was the way most people ran .Net code cross-platform since 2004.
We will need mono to work along with DNVM and DNX to get our environment set up.
Run ```brew install mono``` from the command line to install the latest version of mono from Homebrew.
(We can later update it along with our other Homebrew installed applications all at once by running ```brew update```)

###DNVM###
The DNVM (DotNet Version Manager) is responsible for keeping track of the version of the .Net runtime environment that you currently have installed.
It allows you to use multiple versions for different projects, and switch back and forth as needed.
Type the following in to your terminal:

```
brew tap aspnet/dnx
brew update
brew install dnvm
```

This will add the dnx repository (it's not a set of the default repositories for homebrew, so we add it to let it know where to look when we ask it to install dnvm, otherwise it wouldn't be able to find it).

###DNX###
The DNX (DotNet eXecution environment) is a set of tools used for running .Net programs.
It includes a compilation system, SDK tools, and a native CLR host. 
These tools will translate the C# code we will right into CLR (Common Language Runtime) bytecode for the virtual machine to run, SDK tools to help 
To install the DNX, run ```dnvm upgrade```
This will tell the DNVM to grab the latest version of the DNX.

###Making Sure it Just Works<sup>TM</sup>###
One of the frustrating parts about learning is when you follow the instructions completely and things just don't work. 
It's enough to make someone quit.
Since that's the opposite aim of this article, let's download some source code (using git) and make sure that it runs.
When setting up my environment, I actually ran into a couple errors that I had to fix before I could run the sample applications.
I'll show you the steps that it took for me to get my environment running, and then give some tips on how to troubleshoot these kinds of problems.

####Grab the source####
I always like to make a directory for the different languages I mess around with.
We can make one and change into it before we start:

```
cd ~
mkdir -p projects/cs
cd projects/cs
```

or just

```mkdir -p ~/projects/cs/ && cd ~/projects/cs```

Next, we'll clone the sample code from the aspnet repository on github

```git clone https://github.com/aspnet/Home.git```

####Test out the samples####
Now we'll change into the directory for the sample projects one by one, making sure that we can run each of them.

First the console application:

```cd Home/samples/1.0.0-beta4/ConsoleApp```

Then we'll need to grab all of the library references needed for the application to work

```dnu restore```

Then run the application

```dnx . run``` (This is how we run applications that don't need a web host)

Next the web application:

```
cd ../HelloWeb
dnu restore
dnx . kestrel
```

That last line shows how we run web applications. 
Kestrel is the server that servs up the web pages when the url is requested.
Open up a web browser and go to [http://localhost:5004/](http://localhost:5004/) to make sure you see the aspnet welcome page.
Once you've verified that it's working, go back to the terminal and hit the return/enter key to close the server.
Unlike most servers, if you hit control-c, it will just lock up.
If this happens, you can background the process with control-z, then run ```jobs -l``` to find the pid and use the kill command to stop the server.

Lastly, the MVC web applications:

```
cd ../HelloMvc
dnu restore
dnx . kestrel
```

aaaaaand here's where I get my first error.
For me it looks like this:

```
TypeLoadException: Could not load type 'Microsoft.Framework.Runtime.Compilation.ILibraryExport' from assembly 'Microsoft.Framework.Runtime.Interfaces, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null'.
System.Lazy1[System.Collections.Generic.List1[Microsoft.CodeAnalysis.MetadataReference]].CreateValue () [0x00000] in , line 0
```

First thing I did was look at the github issues page.
There was someone else having the same problem, so between us and the maintainer we were able to figure out the issue and help others at the same time.
[https://github.com/aspnet/Home/issues/515#issuecomment-98030542](https://github.com/aspnet/Home/issues/515#issuecomment-98030542)

The error was referring to a library that couldn't be loaded.
The fix was to specify the exact type in the project.json file so it wouldn't try to load a different, later version.
After that, it loaded up fine.

For reference, when I run into an issue, I:

* Check the github issues page
* Check stackoverflow
* Google

###Visual Studio Code###
Now that the code is working, let's get our IDE installed.
Follow the instructions at [https://code.visualstudio.com/](https://code.visualstudio.com/) and let's continue on to [Part 3]()

