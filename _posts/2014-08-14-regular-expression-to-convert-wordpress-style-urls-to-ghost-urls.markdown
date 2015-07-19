---
author: tjones
comments: false
date: 2014-08-14 23:19:37+00:00
layout: post
slug: regular-expression-to-convert-wordpress-style-urls-to-ghost-urls
title: Regular Expression To Convert Wordpress Style Urls to Ghost Urls
wordpress_id: 1209
categories:
- old
tags:
- Old
---

It took me a while to come up with a regular expression to convert wordpress urls (index.php/year/month/day/title) to the ghost urls  This is the corrosponding redirect line in my Nginx config. 





rewrite "/index.php/([0-9]{4})/([0-9]{2})/([0-9]{2})/(.*)" /$4 permanent;
