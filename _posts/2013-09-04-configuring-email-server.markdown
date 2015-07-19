---
author: tjones
comments: false
date: 2013-09-04 07:21:46+00:00
layout: post
slug: configuring-email-server
title: 'Some Old Notes: Configuring a Email Server with Iredmail and Ubuntu 12.04'
wordpress_id: 1001
categories:
- old
tags:
- Download Ired Mail
- Old
- Untar Ired
---

Install Iredmail

See the Iredmail documentation [http://www.iredmail.org/install_iredmail_on_ubuntu.html](http://web.archive.org/web/20141115122245/http://www.iredmail.org:80/install_iredmail_on_ubuntu.html) for more details

First install bzip2

_apt-get install bzip2_

Edit first line of /etc/hosts

_nano /etc/hosts_

To read like the following



<blockquote>127.0.0.1       mail.theojones.name localhost mail

</blockquote>



Download Ired Mail

wget [https://bitbucket.org/zhb/iredmail/downloads/iRedMail-0.8.5.tar.bz2](https://bitbucket.org/zhb/iredmail/downloads/iRedMail-0.8.5.tar.bz2)

Untar Ired mail.

tar xjf iRedMail-0.8.5.tar.bz2

**Add forwarding**

Go to [https://mail.theojones.name/phpldapadmin/htdocs/cmd.php](https://mail.theojones.name/phpldapadmin/htdocs/cmd.php)
