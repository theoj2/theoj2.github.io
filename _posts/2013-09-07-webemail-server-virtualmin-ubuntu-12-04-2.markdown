---
author: tjones
comments: false
date: 2013-09-07 20:03:20+00:00
layout: post
slug: webemail-server-virtualmin-ubuntu-12-04-2
title: Web/Email Server Configuration With Virtualmin on Ubuntu 12.04
wordpress_id: 1007
categories:
- old
tags:
- Add Domain Name
- Configure Virtualmin
- Old
- PHP
- VPS
---

I have recently moved the VPS that this blog is hosted on to a Virtualmin install on Ubuntu 12.04. This tutorial shows how I have configured it. Virtualmin is a free program that can install and manage common server services. Among other things it can manage email (defaulting to the

postfix/dovecot servers), web (defaulting to Apache), and mailing lists (using [GNU Mailman](http://www.gnu.org/software/mailman/)). For this tutorial I will assume you have a working Ubuntu 12.04 install. I am using the free/open source GPL licensed version of Virtualmin instead of the proprietary version.

<!-- more -->



### Install Virtualmin and Dependencies



Virtualmin's developers have produced a script that installs Virtualmin and all of its dependencies. Download the install script with the following command.

_wget [http://software.virtualmin.com/gpl/scripts/install.sh](http://software.virtualmin.com/gpl/scripts/install.sh)_

Run the script to install Virtualmin and its dependencies.

_/bin/sh install.sh_

Wait while Virtualmin updates and installs.



### Create a Swap File



Some of the components of the Virtualmin system can cause peaks of memory usage that can overfill the system ram on some low memory installations.The spam and virus checking programs (Spamassin and ClamAV) used by Virtualmin are particularly likely to cause peaks of RAM usage. For this reason, it is a good idea to create a swap file if you haven't created a swap partition during your install of Ubuntu.Most images distributed by VPS hosts do not include swap space. Run the following commands to create a 1GB swap file.

_fallocate -l 1000M /swapfile_

_chmod 600 /swapfile_

_mkswap /swapfile_

Set the swap file to load on boot by adding a line to /etc/fstab

_Nano /etc/fstab_

add

_/swapfile none swap defaults 0 0_



### Common PHP Extensions



Curl and PHP5-gd are common PHP extensions that many PHP applications require. Install them with the following commands.
_apt-get clean && apt-get update && apt-get install php5-curl_

_apt-get install php5-gd_



### Configure Virtualmin



Now we have a Virtualmin install with all dependencies. Now it is time to configure Virtualmin.

Go to https://<YOUR IP HERE>:10000/ and run through the Virtualmin configuration wizard.

In my experience, the default PHP upload file size limit is too low for many applications. Change the upload settings with the following procedure. Under Services find "PHP 5 Configuration". Then click "Resource Limits".Edit the "Maximum file upload size" textbox. Save your changes.

[Greylisting](http://en.wikipedia.org/wiki/Greylisting) is a powerful anti-spam technique that exploits the fact that spammers rarely use standards compliant email servers.The standards for the email protocol allow the receiving server to declare that it is temporarily unavailable instead of outright accepting or rejecting a message. If this happens a standards compliant server will wait and then resend the message.Most spambots will not. Greylisting configures the mail server to declare that it is temporarily unavailable the first time that a server that has never delivered an email to you attempts to send an email. Greylisting may delay some of your email but it is one of the most effective anti-spam methods. To enable it follow the following steps.
Under "Email Messages" find "Email Greylisting".Click "Install Greylisting". Under "Email Messages" find "Email Greylisting". Click "Enable Greylisting".

DKIM is another anti-spam technique that attempts to filter out spoofed email headers. To enable it follow the following steps. Under "Email Messages" find "DomainKeys Identified Mail". Click "install DKIM".



### Add Domain Name



You now have a fully configured Virtualmin installation. To add a domain name to it follow the following steps  Click "Create Virtual Server". Fill out the form that appears.
