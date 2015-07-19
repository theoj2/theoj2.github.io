---
author: tjones
comments: true
date: 2014-12-29 06:36:40+00:00
layout: post
slug: client-side-data-validation-or-how-security-flaws-can-get-into-software
title: Client Side Data Validation; or How Security Flaws Can Get Into Software
wordpress_id: 1286
categories:
- old
tags:
- Image Via Flickr
- Stack Exchange
---

There is a reason why attacks like the Sony breach still happen. Hacking is fundamentally about having the creativity and knowledge to put well known methods together into a well designed overall line of attack. The things that hackers exploit are mistakes that are easy to make, and the people who build a network have to get lucky all the time. But the people attacking it have to just

[caption id="attachment_1318" align="alignright" width="226"][![Image Via Flickr (user sylvar) https://flic.kr/p/3M87z](http://www.theojones.name/wp-content/uploads/2014/12/31436961_33399f4066_o-226x300.jpg)](http://www.theojones.name/wp-content/uploads/2014/12/31436961_33399f4066_o.jpg) Image Via Flickr (user sylvar) https://flic.kr/p/3M87z[/caption]

get lucky a few times. Hacking may involve some technical skill, but the people that crack computer networks have more creativity than technical wizardy. And with the likes of Sony, you can't rule out the possibility of technical incompetence. But there is a reason why these exploits keep being present in the frequency that they do, and that reason is simple -- programmers and network designers don't know security and thereby make even very simple errors in the systems they design. One simple error is client side validation, trusting a calculation made on a remote device that could be completely under the control of an attacker. The problems with this type of design is clear, programmers are putting their security on the hacker's computer, but this error keeps on being made. Take this thread on Stack Exchange for instance [http://security.stackexchange.com/questions/76974/verify-client-side-created-data](http://security.stackexchange.com/questions/76974/verify-client-side-created-data)

The OP in question here has a simple issue. "_I have a Java applet, which records the whole screen of the user and uploads the images to the server. If one would be able to (and many people could, I know) falsify the screen recording they could cheat legitimate users of the system out of their money, so there are incentives._". The problem, of course, is that there is no way to make that type of design secure. Since the java applet is under the user's control, a user could make any change to the screen shot. A design that relies on the proper behavior of a remote system is inherently insecure. But such designs keep being made.
