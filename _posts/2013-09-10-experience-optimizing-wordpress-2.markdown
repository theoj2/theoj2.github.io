---
author: tjones
comments: false
date: 2013-09-10 08:58:05+00:00
layout: post
slug: experience-optimizing-wordpress-2
title: My Experience Optimizing WordPress
wordpress_id: 1013
categories:
- old
tags:
- APC
- CSS
- DNS
- Old
- W3 Total Cache
---

I've been trying various methods to make this blog load faster and optimize WordPress. This post discusses some of what I found works and what I found didn't work.  
One of the first things I tried was W3 Total Cache which many bloggers . This plugin was able to reduce my page load times by about 1 sec, but I decided that it is more trouble than it is worth. It was incompatible with other plugins that I have been using, created issues with page loading and created other issues. If you do decide to use this plugin I recommend that you do not use the minify options as this functionality was in my experience the most likely to cause problems. Also, install the APC module for PHP (on Ubuntu apt-get install php-apc). APC makes the caching run more efficiently.The next thing I did was to reduce the "above the fold content" on my posts and put more of my post content below the read more button. This resulted in a home page that loaded faster. Previously I had the full content of my posts load on the front page, now I limit the part of my posts that show on the front page to the first paragraph.  
<!-- more -->  



I then tried other plugins to make my WordPress faster.The WP-SmushIt is one that I recommend. It reduces the file size of the images that get sent to the readers' browsers. I also recommend Combine JS and Combine CSS which merge the Javascript and CSS files on your website.   

The next thing I did was minimize the external content that loads on this website.Each time you load a widget or image from an outside website you require the reader's browser to make a DNS request. I replaced the twitter widget with a link to my twitter. I also replaced embedded images that load from external websites with locally hosted images.
