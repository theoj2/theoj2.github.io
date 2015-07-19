---
author: tjones
comments: false
date: 2014-02-10 23:41:31+00:00
layout: post
slug: compiling-newlisp-linux-mint-2
title: Compiling Newlisp on Linux Mint
wordpress_id: 1097
categories:
- old
tags:
- Arch Linux Manjaro
- Linux Mint
- Old
---

I installed Linux Mint on my laptop, but the Newlisp interpreter is not as easy to install on that distro as Arch Linux/ Manjaro. The Ubuntu package created by the Newlisp project does not work on x64 Mint, so it has to be manually compiled. There are two dependencies for Newlisp, ffi and readline. They can be installed as follows





sudo apt-get install libffi-devel   

sudo apt-get install libreadline-dev





Libffi is needed for the Newlisp foreign function interface commands, and readline is needed for the Newlisp REPL.





Then compile and install Newlisp





make   

sudo make install




