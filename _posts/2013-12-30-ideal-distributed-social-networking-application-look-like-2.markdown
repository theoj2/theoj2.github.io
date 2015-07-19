---
author: tjones
comments: false
date: 2013-12-30 15:02:36+00:00
layout: post
slug: ideal-distributed-social-networking-application-look-like-2
title: What Would the Ideal Distributed Social Networking Application Look Like?
wordpress_id: 1073
categories:
- old
tags:
- Brad Templeton
- Email Replacement
- Old
- Open Source
- Paul Graham
---

Current centralized social networking websites, such as Facebook have many flaws.They have persistent privacy issues and breaches. Their moderation policies are often problematic and applied arbitrarily. These systems are vulnerable to censorship and government manipulation.

The risks of this to privacy are shown by the NSA leaks. The risks to free speech are shown by how, [when under pressure from the Turkish government Facebook restricted posts advocating Kurdish independence](http://www.dailymail.co.uk/news/article-2238519/Facebook-bans-picture-woman-reclining-bathtub--shows-elbow.html) and "Any attack on Ataturk [Turkey's first president]". With a centralized structure these issues of government interference are almost unavoidable. The nature of these networks also means that there is little ability for the user to modify and customize the interface because all of the code runs on the server, and because this code is not open source. This is part of the reason why Facebook has to roll out interface changes to all users, often with many dissatisfied users. Some projects have tried to improve the Facebook interface by running client-side software that modifies the HTML and JavaScript produced by Facebook, [but this method is error prone](http://socialfixer.com/blog/2013/12/18/social-fixer-is-partly-broken-heres-why/).A distributed social network built around a single protocol that allows different implementations of the system, running on different servers would fix these issues. This network would be like email. You can run your own mail server (like I do) and different mail servers can communicate with each other.You can choose from different email providers. A decentralized social network would lessen all of the issues I discussed. If individuals run their own servers, governments would have a hard time controlling these servers. A decentralized system would allow many different implementations and configurations of the system to run. The users would be allowed to choose from the configuration that best suits their wants. They would also be able to chose from different hosts of the system. In the rest of this post I will discuss the problems with currently produced decentralized systems and the design elements that should underlie a good social networking system.



## What are the problems with current decentralized social networks?



Wikipedia has a fairly exhaustive list of current decentralized social networks. [http://en.wikipedia.org/wiki/Comparison_of_software_and_protocols_for_distributed_social_networking](http://en.wikipedia.org/wiki/Comparison_of_software_and_protocols_for_distributed_social_networking)

I have tried many of these systems and looked into others and none of them fit my needs or are likely to be competitors to Facebook. The largest projects Diaspora,Friendica and StatusNet are very difficult to install and configure. These projects often unnecessarily run their messages through other protocols, such as XMPP. This adds extra complexity to the system and its implementation. Other projects are defunct and have no active development. Others lack critical features and do not plan to add them in the future.



### What does a good network have?



First I will discuss what I think a social networking application is. Then I will discuss the particular traits that one should have.



####  What is a social network?



Social networking applications are at their core messaging systems. They allow people to broadcast a message to a group of friends and/or subscribers to a page. They allow people to communicate with each other through private messages. Social networks create a easy way for users to communicate a profile about themselves. Blogging engines, like Wordpress are often confused with social networking applications



#### Ease of use



The first feature that a good social network should have is ease of use. It should be easy to use the webpage client for the network and it should be easy to install a server for the network. But by easy to use I mean [**easy to learn**, not easy to use without learning](http://www.over-yonder.net/~fullermd/rants/userfriendly/2). Easy to use without learning is the unfortunate interface design methodology employed by many businesses, including Facebook.However, it can most clearly be found in Apple's products and to a lesser extent in Microsoft's. Computers are complex devices and the easy to use without learning design methodology tries to hide this complexity from the user. This design attempts to create smart computers, but dumb users. However,easy to use without learning design hurts users in the long run. It kills the flexibility of a system, it creates software that second guesses the user at every point and this design discourages user learning, churning out "computer illiterate" users.It also adds to software complexity and bloat. The easy to learn design methodology admits that computers are complex. Users are expected to know a bit about how the system works and why they are doing what they are doing. This design allows simple flexible systems which cover many use cases.



#### Simplicity



The corollary of ease of use is simplicity. The network, and the protocol that underlies it should be as simple as possible.



#### Split Layout and Message Data, Keep Layout on the Recipient's Side



One of the reasons that Myspace collapsed is that it allowed users to change the way that their profiles looked to other users. New social networks should clearly avoid this mistake by separating the content messages, statuses and profiles from their layout. A distributed social network should allow each user to apply a theme that sets how the system displays to them but that does not affect the theme and layout shown to other users.



#### ....But allow a Wikitext Style Formatting



However, Facebook went to the opposite extreme and disallowed almost all formatting codes in messages. It is not possible to add a hyperlink to a Facebook status/message, nor is it possible to bold or italicize text.A good alternative to this would be to allow the use of a formatting language like [WikiCreole](http://web.archive.org/web/20150623033701/http://www.wikicreole.org/).



#### Detailed Privacy Settings and Post Clusters



A good social networking application should have much more powerful privacy options. These should revolve around what I call "post clusters". Users should be able to categorize their friends into sub groups and set posts to be only viewable by some of these groups. A large reason why social networks that are targeted at specific purposes, like LinkedIn thrive is in part due to the poor privacy options found in most social networks. People want to broadcast different messages to business colleagues than they want to broadcast to friends. Most social networks do not allow this type of fine grained control, so users instead use different networks for each purpose.

As an additional privacy feature, the ideal social networking system should allow a way to anonymously send messages. The protocol of the network should also allow the use of privacy system, such as Tor.



#### Spam Filtering



Any communications network will have to face the issue of how to deal with spam. A distributed network will have to do this without adding centralization or risking user privacy. In my opinion, the best way to deal with spam would be something along the lines of[ Brad Templeton's throttle relay proposal for email](http://www.templetons.com/brad/spam/endspam.html). This method could be made even more powerful because a new social network would have a completely new protocol that could take into account the spam issue.



#### Built in Encryption



Encryption is necessary for privacy in a modern application. A social network should encrypt all communications between servers. It should also have client side encryption as an option, but because client side encryption can be difficult to use, it should not be mandatory for all users.



#### Extensibility, Plugins and Themes



A distributed social network should have a wordpress-style support for themes and plugins. This would greatly improve the flexibility of the system and would allow it to be customized to fit user needs.



#### Email Replacement



[In an essay Paul Graham notes that email is largely used as a todo list and discusses how this role can be replaced](http://paulgraham.com/ambitious.html).



<blockquote>.... my inbox is a todo list, and email is the way things get onto it. But it is a disastrously bad todo list.

I'm open to different types of solutions to this problem, but I suspect that tweaking the inbox is not enough, and that email has to be replaced with a new protocol.  ....

As a todo list protocol, the new protocol should give more power to the recipient than email does. I want there to be more restrictions on what someone can put on my todo list. And when someone can put something on my todo list, I want them to tell me more about what they want from me. Do they want me to do something beyond just reading some text? How important is it? .....When does it have to be done?</blockquote>



A social networking system would have a-lot of the functionality needed for this to-do list. Therefore, it is possible that a to-do list protocol could be built on top of a well-designed social networking system. Current social networks have displaced much of the messaging role of email. A well-designed one could replace email wholesale.



#### WordPress Style Business Model



I assume that even if it were possible most users would not run their own servers. Therefore, there is a need for a hosted version of the application. How WordPress does could be of inspiration. WordPress provides a opensource content management system that users can run on their own, but also provides a hosted form of the blogging engine (wordpress.com).



#### Split Server and Client



When looking at the description of what a social network is you may see that there are two distinct tasks that a distributed social networking application must complete.




    
  1. A server which handles transmitting messages between programs and other servers. This is a role roughly equivalent to that of an email server.

    
  2. A client which displays and messages in a way that is useful for the user. This is roughly equivalent to the role of an email client, like Thunderbird or Gmail.



These two roles should be two separate programs that are written to work well together.This separates the implementation of a system from its interface. This separation would make many features which would be difficult to implement in a web based client only system easy to implement. Interfaces can become obsolete quickly but protocols can last longer. The email protocol, which was designed in the 1970s is still in use, even though the original clients for email are long dead.A clear separation between server and client will extend the life of a social networking system by expanding its flexibility.



#### New Protocol



Social networks are fundamentally different from other systems. Therefore,a new protocol, one dedicated to running these networks is needed. Many previous attempts to create a decentralized social network have free loaded on already existing protocols. This only serves to create a hard to use, overly complicated system. It does not simplify the work needed to create a social network, but instead makes the lives of their designers more complex.A protocol dedicated to social networks will create a platform that programmers can work with, not against.



#### Open Source



Opensource is the only way to create a decentralized network that avoids all of the pitfalls of a centralized network.
