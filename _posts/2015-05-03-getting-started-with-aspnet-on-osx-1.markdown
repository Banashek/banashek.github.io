---
layout: post
title:  "Getting Started with C# on OSX Part 1: Introduction"
date:   2015-05-03
date-day: 3rd
date-month: May
date-year: 2015
categories: C# ASPNET OSX
---

This article series is designed for newcomers to the aspnet world to get started developing ASP.NET applications on OSX.

First, a little history:

Earlier last year, some members from the Visual Studio team had released a set of tools to include intellisense features into various editors called [Omnisharp](http://www.omnisharp.net/). While Omnisharp was an awesome step in the right direction, it was maintained as a non-microsoft project and seemed to be targeted at advanced text editor users, which made it hard for less adept users to get started with C# in the osx/linux universe. 

Of course there was always Monodevelop and Xamarin studio, but it's not too hard to google how most people feel about the IDE experience compared to its competitors.

So for some time, if you wanted a statically-typed, object-oriented language with garbage collection that was cross-platform, you could try C# on Mono or just use Java with IntelliJ like everyone else.

Last week there was a change to this dilemma however. At Microsoft's [Build](http://www.buildwindows.com/) conference, they revealed the new cross-platform IDE [Visual Studio Code](https://code.visualstudio.com/).

Now anyone can download the IDE and get started developing C# applications that will run on Windows, Osx, Linux, and soon BSD.

The open-sourcing of various libraries leading up to the announcement was good, but not many people actually wanted to develop C# in a text-editor. For statically-typed languages, there is so much power that an IDE can provide. Google guides for setting up vim as a Java IDE if you don't believe me, most of them have an IDE (Eclipse) that backgrounds some processing for vim.

So there's a brief and incomplete history of C# cross-platform tooling, but it should be sufficient to answer why C# hasn't been popular outside of the Windows ecosystem.

Now we'll continue to see how to get up and running with Visual Studio Code and the other cross-platform tooling in [Part Two]().
