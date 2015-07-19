---
author: tjones
comments: true
date: 2015-06-20 08:27:10+00:00
layout: post
slug: why-dedicated-podcast-hosting-services-are-a-dubious-idea
title: Why Dedicated Podcast Hosting Services are a Dubious Idea
wordpress_id: 2395
tags:
- Blogging
- podcast
---

[![12212276953_f2f3530bb7_o-edited](http://www.theojones.name/wp-content/uploads/2015/06/12212276953_f2f3530bb7_o-edited.jpg)](http://www.theojones.name/wp-content/uploads/2015/06/12212276953_f2f3530bb7_o-edited.jpg)

As you may have noticed, I have been working on a podcast feature for this blog. However, I am not hosting it on a podcast hosting service. Why? The cost of it isn't worth the benefit. I looked at some podcast hosts, such as [libsyn ](http://libsyn.com)and [Blubrry](https://www.blubrry.com/). These services have advocates (See, for instance http://theaudacitytopodcast.com/best-podcast-hosting-tap133/) but I think there are better alternatives. Now, it is true that regular webhosting is a very bad idea for podcasts. Web servers like Apache tend not to be designed for the types of large file downloads that podcasts bring and they often use hardware (like SSDs) that isn't suited for bulk storage of large files. My alternative to dedicated hosts is object storage services, like [Amazon's S3 ](http://aws.amazon.com/s3/)and Dreamhost's [DreamObjects](https://www.dreamhost.com/cloud/storage/). Objectors to this will note that they charge for bandwidth. But do the math. The cheapest feature-rich podcast hosting service that I am aware of is libsyn's $5 per month plan. It provides 50mb of hosting, but with unlimited bandwidth. DreamHost will sell you 40gb of storage (which is quite plentiful) for $0.95 with bandwidth at 5¢/GB. Amazon's prices are similar (I use dreamhost, but have no strong preference between the two services). How many users will you need to come out worse with DreamObjects? Quite a few. Lets say you use your full libsyn 50mb and your subscribers download everything you post. You pay $5. For comparison a DreamObjects user could afford storage plus 80gb of bandwidth. Under these assumptions a Dreamhost user could support 1,600 users before libsyn looks better. In fact, services like libsyn are able to support the few heavy users because the vast majority of their users use less than they pay. The great majority of their users support the few.

Image credit: [www.ilmicrofono.it](https://www.flickr.com/photos/115089924@N02/12212276953/in/photolist-jBa7tc-6prPij-mQTZzo-qwt19h-mQSo9p-95JuwJ-5y3xN1-e3VdRk-dXa6e3-h4G51-qyXa6k-fTfmCa-bfaLPK-kzwSkU-dRDAP1-fxy4rr-kzv7gT-kzwRQL-kzv6Jk-byoNNs-4p9A6w-mqSacg-dXqqju-dXjKCr-dXjKzK-kq9Qh-dG84CM-pBZ4Qv-b95QtF-4cmWDY-fhAY2c-fxNnXw-jetB8o-aFNjYr-4XNY7C-f8SoY5-aBqp7k-6bVXQt-4yLdDU-6xPfo9-984ZGT-eAjZ59-hYu4UY-pBZ6ov-fxNo2h-hqG3GV-6niihH-6hSRQJ-7KJGnA-aapeHV#)


