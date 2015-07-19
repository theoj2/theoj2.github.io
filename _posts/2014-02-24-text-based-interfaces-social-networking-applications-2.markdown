---
author: tjones
comments: false
date: 2014-02-24 23:45:03+00:00
layout: post
slug: text-based-interfaces-social-networking-applications-2
title: Text Based Interfaces and Social Networking Applications
wordpress_id: 1109
categories:
- old
tags:
- GUI
- Old
---

I've been thinking about what the best interface for a social networking program would be. [As I noted ](http://web.archive.org/web/20140403093812/https://theojones.name/index.php/2013/12/30/ideal-distributed-social-networking-application-look-like/)in a post a while ago about social networks.

A good social network should be easy to use. It should be easy to use the client for the network and it should be easy to install a server for the network. But by easy to use I mean [**easy to learn**, not easy to use without learning](http://www.over-yonder.net/~fullermd/rants/userfriendly/2). Easy to use without learning is the unfortunate interface design methodology employed by many businesses, including Facebook. However, it can most clearly be found in Apple’s products and to a lesser extent in Microsoft’s.

Computers are complex devices and the easy to use without learning design methodology tries to hide this complexity from the user. This design methodology can only exist by limiting flexibility and by taking away possibilities. This design attempts to create smart computers, but dumb users. However, the easy to use without learning design hurts users in the long run. It kills the flexibility of a system, it creates software that second guesses the user at every point and this design discourages user learning, churning out “computer illiterate” users. A program can only be easy to use without learning if it is simplified enough that many of the most powerful features of the system are reduced.  It also adds to software complexity and bloat. The easy to learn design methodology admits that computers are complex. Users are expected to know a bit about how the system works and why they are doing what they are doing. This design allows simple flexible systems which cover many use cases.

What UI design is best able to create a social networking system that is easy to learn, without nerfing the system into a easy to use without learning design. Oddly enough, I have come to the conclusion that it  may be the command line. CLIs are not dead interfaces and have many benefits over GUIs for many applications. They require the user to learn more to use , but are much more powerful. I will discuss these general benefits, and then go into some specifics about what a command line for a social networking program would work, and how such an interface could be integrated into a social networking system.

<!-- more -->Command line interfaces are not dead. The Linux operating system still makes heavy use of them (in fact my laptop does not have a full desktop environment or GUI file manager installed, instead I use a mix of a tiling window manager and terminal applications). Command lines are a core interface of this operating system, and the Unix philosophy that drives the design of Linux and other modern UNIXes (["_This is the Unix philosophy: Write programs that do one thing and do it well. Write programs to work together. Write programs to handle text streams, because that is a universal interface.")_](http://en.wikipedia.org/wiki/Unix_philosophy). GUIs . CLIs are[ becoming increasingly popular on web applications too](http://www.hanselman.com/blog/WebSitesWithEmbeddedCommandLinesYouGotYourCommandLineInMyInternet.aspx).
