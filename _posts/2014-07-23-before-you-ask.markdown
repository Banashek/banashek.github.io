---
layout: post
title: "Before you ask, do you really understand the problem?"
date: 2014-07-23 12:30:53 -0700
date-day: 23rd
date-month: July
date-year: 2014
---
You've got a problem that needs fixing. You don't know exactly what's going on, but there is something wrong. Perhaps the sink faucet is leaking and the "drip, drip, drip" is giving you headaches. Maybe your Visual Studio can no longer debug your application. Or your chicken keeps coming out more cooked on the outside than the inside when using a pan. These are three problems I had recently. And the solution to each of them began the same way: by increasing my functional domain knowledge. This is such an important and rarely spoken about skill that the mere recognition of the lack of its existence in your life can lead to an increase in skill in any domain. Let me tell you how I used it to solve my problems.

I'll begin with a couple quotes:
<blockquote>
<p>[I do not] carry such information in my mind since it is readily available in books. ...The value of a college education is not the learning of many facts but the training of the mind to think.</p>
<p><i>- [Albert Einstein](http://en.wikiquote.org/wiki/Albert_Einstein)</i></p>
</blockquote>

<blockquote>
<p>...I'm going to give you the honest answer. Your problem is that you lack the functional domain knowledge to ask a significant question...</p>
<p><i>- Random redditor, In response to an unclear question</i></p>
</blockquote>

The former of the two has been attributed to many a terrible argument. In my experience many people use it as an excuse for ignorance. "Why would I need to know how X works if I can just look it up?" This might work for a superficial issue or upper layer problem, but for anything with even 1 more layer of complexity above the top this is a losing strategy. The latter of the two quotes was a response to someone asking a question regarding IT infrastructure with no knowledge of how the infrastructure actually worked. They wanted a complex problem fixed without having to know any of the details of the problem or the solution.

Herein lies the problem: You don't understand the problem. It's not your fault (hopefully). Something has happened in a domain you are unfamiliar with. So how do we approach the problem? There are a couple approaches that come to mind:

1. If there is someone around with the domain knowledge required to solve the problem, you can go ask them. This is the case most of the time between people of different specializations within a company (i.e. User asks technical support why something isn't working). This kind of solution is fine in most situations where a weird issue is occuring that is far removed from your knowledge and you don't see the aquisition of the domain knowledge as valuable.
2. The problem is something that lies close to your domain, or a domain you should probably be familiarizing yourself with (i.e. a DNS problem that a sysadmin is experiencing. Might not be their specialty, but it definitely lies in their realm most of the time). In this instance the investment into familiarizing yourself with the domain (in this case figuring out how DNS works) should be made a priority. Once you have enough domain knowledge, the actual issue should make itself clear and you can fix it (or notify those responsible for fixing it if the issue is out of your control). Again, this is appropriate if you are responsible (or wanting to learn) something related to the target domain.

Alright, so we learn about the the area in which the problem could be occurring and notify the responsible party to get it fixed. In the first example, the user called support to fix a part of the application that turned out to be a bug. The bug was reported, the application updated, and the issue fixed without the user having to learn the intracacies of computer science. Perfect. Our second example was solved by the system administrator who, after researching DNS, learned that it was actually a networking problem which he knew how to fix already. The DNS knowledge was valuable however, because it helped him to _identify_ the problem.

Now, here's the cool part about all of this. For problem solving, most people can tell when they're responsible enough to need to figure something out, even if minimally, to fix the problem at hand. The situation in which I believe this is least understood is when someone is embarking on an adventure to _learn something new_. I know, give me just a few minutes of your time and I'll explain. 

A lot of people want to learn a lot of things. This is fantastic. I love learning new things in various domains, technical or otherwise. But a lot of the time someone will get stuck because they don't know how to learn something. Functional domain knowledge is important to learning specifically when people want to learn something that is N steps away. An example of this is "I want to learn how to hack". If you've ever been on a technology forum of some sort, you've seen this question pop up. So what's the problem with the question? 

The question implies a lack of understanding of the functional domain. "I want to learn how to hack". Ok. Define hacking. There are multiple definitions, and even if we take the standard definition of cracking/breaking/etc of computers/applications/whathaveyou, it still isn't specific enough. Do you want to learn Web application pentesting, reverse engineering of systems applications, network security? Those are 3 of many different sub-specialties, each with sub-specialties below them. So let's say Johnny Hacker wants to learn to "pwn the facebooks". We'll categorize his goal as becoming employed as a web application penetration tester. Next, let's define the functional domain distance between him and that goal. 

(Feel free to skim these lists to get to the rational afterwards)

For working in security of any type, basic requirements would be: 

1. Learning the domain
2. Learning the security of the domain
3. Learning the tools and techniques to exploit the vulnerabilities in the domain
4. Learning the legality and procedures for carrying out such pentests

For the first requirement, Johnny will need to learn:

1. Programming fundamentals for web applications (php/html/css/js in this example)
2. How the web works (http, sessions, cookies, authentication, digest mechanisms, etc)
3. Web application development (let's give him laravel 4 as a modern framework to work with, and wordpress as a modern CMS to work with)
4. Web application design development (what I mean here is modern css/javascript usage (jquery, angular, bootstrap, etc))
5. How to host this (should we give him a easy hosting provider, or add 5+ more bullets for learning how to setup/admin a LAMP stack?)
6. A development workflow (editor, linter, deployment techniques, ide, testing suite, whatever else is required)

For the second requirement, Johnny will need to learn:

1. The history of basic web application security (hacking exposed web applications + wikipedia?)
2. The evolution in defensive and offensive techniques
3. The current state of application defense/offense (this can get complex and require other domain knowledges such as DNS/networking/operating systems & security)

For the third requirement, Johnny will need to learn:

1. A scripting language (ruby/python/perl/whatever)
2. Common web application penetration testing tools (Burp suite, ZAP, w3af, Acunetix, skipfish, etc)
3. Networking/proxies other methods of masking

For the fourth requirement, Johnny will need to learn:

1. The law in regards to the area that Johnny will be working.
2. How to set up a personal lab to learn these things initially (virtualization, basic system/network administration, etc)
3. How web application penetration tests/vulnerability assesments are typically carried out
4. How to write reports/findings

Great. So that is a very incomplete but general idea of the steps Johnny needs to take. I have left out quite a few lists/skills for the sake of completing this article in one sitting. However, we are now able to define the path that Johnny would need to follow to attain his goal. If we add up the requirements, Johnny is 16 functional domains away from being a competent _Entry Level_ web application penetration tester and being able to ask significant questions regarding the domain. 

Now let me tell you how I solved my three problems.

1. My leaky faucet was caused by a washer that needed replacing. Before hand I thought that my faucet was just a pipe with a piece of metal to open and close the connection. Now I understand how it is constructed and functions better, and from that knowledge have gained an understanding about how a few other water appliances in my house function.
2. I'm used to vim/unix tools for development. I researched Visual Studio and found out that it attaches the remote debugger to MSVmon.exe (the debugger monitor) to debug applications. Somehow a firewall rule was changed that had blocked MSVmon.exe from communicating. Re-opening the firewall rules fixed the issues and taught me a little bit more about windows firewall rules, Group policy updates, and Visual Studio.
3. If you cook something on too high of a heat, it gets cooked on the outside more than the inside. Reading up on convection/conduction and different oil types helped my chicken come out just the way I wanted it to.

So if I could leave with some advice on problem solving, it would be:

*  Define your problem
*  Identify any gaps in knowledge of the domains involved with the problem
*  If you are responsible for the problem, research the domains until you are able to fix it.
*  If you are not responsible for the problem, identify the party responsible for implementing the fix (and optionally learn about the domain anyway to expand your knowledge).
