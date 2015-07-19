---
author: tjones
comments: true
date: 2015-05-30 07:05:50+00:00
layout: post
slug: on-reducing-blogging-engine-bloat
title: On reducing blogging engine bloat.
wordpress_id: 2274
tags:
- Blogging
- Ghost
- UNIX
- UNIX Philosophy
- WordPress
---

I've switched between blogging engines a few times for this site (there are still some broken links and images from the transition). WordPress, what I'm on now, has a good bit of bloat. Simpler blogging engines, like Ghost, go too far in the other direction, and lack critical features.  I haven't been able to find a blogging engine that hits a good in-between. Personally, I feel that the way to hit that in-between in modularity.  The old UNIX Philosophy of "do one thing and do it well". Plugins are how modularity should be reached. Create a simple core blogging engine (the functionality level of Ghost would be a good target) and add the rest as optional plugins. Now, you might note that WordPress plugins often add a lot of bugs, have a lot of security holes, and are often written by people who don't know what they are doing. And you would be right. However, there is no reason why such plugins can't be maintained in the same source tree as the core software with the help of actual developers. Just put any frequently used plugin in the tree as an officially supported feature set. A user can also easily swap out the official implementation of a feature with an alternative.   This would provide the perfect mix of flexibility and simplicity.  It would allow more officially supported features but users who don't want a feature don't have to put up with the BS that comes with it.  This is a rough analogue of the development method of the classical UNIXes and the BSDs.
