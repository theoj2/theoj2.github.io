---
author: tjones
comments: false
date: 2015-03-18 17:48:14+00:00
layout: post
slug: windows-memory-management-is-terrible-or-how-to-deal-with-system-lockups-associated-with-extreme-disk-activity-usage
title: Windows' Memory Management is Terrible -- or How to Deal With System Lockups
  Associated With Extreme Disk Activity Usage
wordpress_id: 1817
categories:
- Science and Tech
tags:
- Control Panel
- RAM
---

I've been having an issue with a[![Capture](http://www.theojones.name/wp-content/uploads/2015/03/Capture-300x261.png)](http://www.theojones.name/wp-content/uploads/2015/03/Capture.png) temporary freeze of my Windows 8.1 computer followed shortly by very high disk read-write activity. I took a while, but I pinned the issue down to swapping. In short, the memory management on Windows is terrible compared to that of Linux. And a Windows computer (or at least mine) will start swapping if you look at it the wrong way -- even if there are gigabytes of RAM left. The only way to fix this is to eliminate the swap file. This should be only done if there is a lot of ram on the system in question -- because if RAM runs out while swapping is off programs are going to crash.

To turn off swapping do the following: 
 1. Go to the Control Panel.  Find All control panel items > System
 2. Click on "Advanced system settings"
 3. Under performance, click on "settings"
 4. Go to the "Advanced" tab
 5. Under Virtual memory, click on Change
 6. Disable the "Automatically manage paging file size for all drives" check box
 7. Zero it out.
