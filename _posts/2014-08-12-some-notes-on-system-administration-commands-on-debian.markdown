---
author: tjones
comments: false
date: 2014-08-12 04:25:29+00:00
layout: post
slug: some-notes-on-system-administration-commands-on-debian
title: Some Notes on System Administration Commands on Debian
wordpress_id: 1203
categories:
- old
tags:
- Old
- Re-attach Screen
- Restart Nginx
- Start Screen
- Website Speed Test
---

**Restart Nginx**





/etc/init.d/nginx restart





**Website Speed Test**





[http://tools.pingdom.com/fpt/](http://tools.pingdom.com/fpt/)





**GNU Screen Tutorial**   

[https://www.linux.com/learn/tutorials/285795-taking-command-of-the-terminal-with-gnu-screen-](https://www.linux.com/learn/tutorials/285795-taking-command-of-the-terminal-with-gnu-screen-)





<blockquote> 
For an easy reference, here's a list of the most common screen commands that you'll want to know. This isn't exhaustive, but it should be enough for most users to get started using screen happily for most use cases.

Start Screen: screen  
Detatch Screen: Ctrl-a d  
Re-attach Screen: screen -x or screen -x PID  
Split Horizontally: Ctrl-a S  
Split Vertically: Ctrl-a |  
Move Between Windows: Ctrl-a Tab  
Name Session: Ctrl-a A  
Log Session: Ctrl-a H  
Note Session: Ctrl-a h  
</blockquote>





**MySql Config Wizard**   

[https://tools.percona.com/wizard](https://tools.percona.com/wizard)





**MySQL Database Creation**   

[http://www.debuntu.org/how-to-create-a-mysql-database-and-set-privileges-to-a-user/](http://www.debuntu.org/how-to-create-a-mysql-database-and-set-privileges-to-a-user/)





To login:   

 mysql -u root -p
To Create DB :   

mysql> create database exampledb;   

Create User:   

mysql> grant usage on _._ to user@localhost identified by 'passwd';   

mysql> grant all privileges on exampledb.* to user@localhost ;
