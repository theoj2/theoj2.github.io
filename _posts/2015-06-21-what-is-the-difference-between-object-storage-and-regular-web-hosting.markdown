---
author: tjones
comments: true
date: 2015-06-21 00:43:39+00:00
layout: post
slug: what-is-the-difference-between-object-storage-and-regular-web-hosting
title: Top Five Differences Between Object Storage and Regular Web Hosting
wordpress_id: 2411
tags:
- object storage
- web hosting
---

[![objectstorage](http://www.theojones.name/wp-content/uploads/2015/06/objectstorage-300x225.jpg)](http://www.theojones.name/wp-content/uploads/2015/06/objectstorage.jpg)In response to[ yesterday's post on podcast hosting](http://www.theojones.name/why-dedicated-podcast-hosting-services-are-a-dubious-idea/), I got a comment stating the flaws of regular webhosting for hosting podcasts. I agree with him that regular hosting is pretty bad for hosting large files like podcasts. My alternative is object storage services (S3, DreamObjects). These are designed to host large files. Sure, they usually charge for bandwidth. But its usually something small like five cents. And you will need viewers in the thousands for that to be substantial. And I would bet that there is some confusion between object storage and regular webhosting. So, in this post I will clarify the difference.




    
  1.  **Pricing regular webhosting charges a flat monthly fee** Object storage charges based on usage.

    
  2.  **Metered versus unmetered storage and bandwith** Object storage meters things like storage and bandwidth. Regular webhosting usually allows "unlimited" storage and bandwidth, but with limits on acceptable use of this storage and bandwidth.

    
  3. ** Dynamic versus static content** Object storage only holds static content (mp3s, videos, large files, html documents, etc). Full webhosting supports dynamic content (php, python, etc). You won't be able to install WordPress on object storage, but you will be able to do so on webhosting.

    
  4. **Suitability for a website** You won't want to host your root website on a object storage system because the file names are often not suited to such a use Ie. https://objects.dreamhost.com/theopodcasts/uber_01_01.mp3 (which is the url of one of my podcasts) But hosting full websites its the purpose of existence for webhosts

    
  5. **Suitability for large files and backups  **Due to both hardware limitations of the servers allocated to web hosting, the software they use, and the limitations imposed by TOS agreements webhosting is poorly suited to storage large files. Hosting large files, however, is pretty much the point  of object storage. Likewise, you shouldn't backup to your webhost, but object storage providers often explicitly market to the backup market (see, for instance, [Amazon's Glacier service](http://aws.amazon.com/glacier/))



In short, object storage won't be your main presence on the net, but it can store some of your larger files.

Image credit: https://flic.kr/p/GkXFw
