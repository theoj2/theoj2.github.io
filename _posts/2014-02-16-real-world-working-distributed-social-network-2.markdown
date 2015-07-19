---
author: tjones
comments: false
date: 2014-02-16 22:55:01+00:00
layout: post
slug: real-world-working-distributed-social-network-2
title: A Real World and Working Distributed Social Network
wordpress_id: 1105
categories:
- old
tags:
- HTML
- Linux Mint
- Old
- Shamir Secret Sharing
---

About a month ago I discussed [the need for a distributed social networking](http://web.archive.org/web/20140403093812/https://theojones.name/index.php/2013/12/30/ideal-distributed-social-networking-application-look-like/) application. At the time I wrote that article there were no social networking systems around that were reasonably easy to install, secure, and with a usable feature set. I just found out about[ a new application, Twister, that ](http://twister.net.co/)comes close to meeting these goals. Its open source, and it seems to be easy to write software that interfaces with it. It is fully decentralized and its server can run on a regular computer without the need for an always on server.  Its main flaw seems to be that there is no way to to run a web based interface for it from a remote computer. This means that it is currently impossible to have a website that you can just go to and register an account at without installing anything on your computer. However, I have done a bit on coding over the weekend and I think this issue is pretty tractable. I have written an application in Python that can allow users to view Twister profiles over the web and I have , eventually I will post this code, and time permitting I may turn this into a full hosted web based interface for Twister that accounts can be registered at. In the rest of this post I will discuss some of the flaws and possibilities with this network. I will then discuss how to install it on Linux Mint (still not as easy a process as it could be).  

<!-- more -->

The other clear limitation of Twister is that it has adopted the 140 character  limit from Twi**_tt_**er. This limits the depth and nature of the posts that can be made with this system. There are reasons to limit the size of messages, but 140 is too low. A social networking system should allow enough text to put a link with a solid paragraph of text. I reckon this would be about a limit of 1000 characters.

There is also no support for anything like Facebook's groups.This issue seems easy to code around because it would possible to just create a program that manages a page that posts out the content of any private messages sent to it. This program would also need to have the appropriate measures needed to drop the banhammer on the occasional idiot. This program would work in a similar way to GNU Mailman or other email mailing list managers.

The private messaging features in twister are weak. It does not allow anyone who you are not already following to message you, but in any messaging system there are reasons to want the ability to message people that you have not already been in contact with. It is harder to code around this issue, but the use of relays that people can follow may be one way to code around this limitation.It may even be true that private and public messaging is so totally different that it would be better to write separate application to handle each task.

Profiles have very few options.

The loss of a private key means the loss of your profile. There therefore needs to be a way to back up this key. A program that uses Shamir's Secret Sharing or a similar algorithm to split a backup of the key into pieces and then distributes these pieces among the user's friends  may be one easy way to resolve these issues.

I have found that the best way to interface with the Twister RPC is not through the Twister author's suggested python-bitcoin (which is really just a JSON RPC client) ,but instead is through the pyjsonrpc library. Here is some Python code to grab the contents of user profiles and format it into HTML that I wrote with this library: (wordpress doesn't seem to handle the formatting of python code very well, eventually I'll create a GitHub repository for this).

http_client = pyjsonrpc.HttpClient(   

url = "http://localhost:28332",   

username = "user",   

password = "pwd"   

)

def GetRawProfileJSON(UserNameToLookUp):   

return http_client.call("dhtget", UserNameToLookUp, "profile", "s")   

def GetParsedProfileJSON(UserNameToLookUp):   

return GetRawProfileJSON(UserNameToLookUp)[0]['p']['v']

def GetFullNameHtml(ParsedProfileJSON):   

global PageTitle   

FullName = ParsedProfileJSON['fullname']   

PageTitle = FullName + "  Profile"   

return "<h1>Name</h1> <h2>" + FullName + "</h2><br></br>"   

def GetUrlHtml(ParsedProfileJSON):   

url = ParsedProfileJSON['url']   

return "<h1>Website</h1> <h2>" + url + "</h2><br></br>"   

def GetLocationHtml(ParsedProfileJSON):   

loc = ParsedProfileJSON['location']   

return "<h1>Location</h1> <h2>" + loc + "</h2><br></br>"   

def GetBioHtml(ParsedProfileJSON):   

bio = ParsedProfileJSON['bio']   

return "<h1>About Me</h1> <h2>" + bio + "</h2><br></br>"

def GetProfileHTML(UserNameToLookUp):   

parsed = GetParsedProfileJSON(UserNameToLookUp)   

return GetFullNameHtml(parsed) + GetUrlHtml(parsed) + GetLocationHtml(parsed) + GetBioHtml(parsed)



Installing this program is easier than most other distributed social networking apps but still a pain. Here is how I did it on Linux Mint.

sudo apt-get install git

sudo apt-get install autoconf

sudo apt-get install automake

sudo apt-get install libtool

sudo apt-get install g++

sudo apt-get install libboost-all-dev

sudo apt-get install libssl-dev

sudo apt-get install libdb5.3++ libdb5.3++-dev

sudo apt-get install miniupnpc

sudo apt-get install libminiupnpc-dev

sudo apt-get install libglibmm-2.4-dev

git clone [https://github.com/miguelfreitas/twister-core.git](https://github.com/miguelfreitas/twister-core.git)

cd twister-core

./bootstrap.sh

./configure --enable-logging --enable-debug

make

make will take a while

mkdir ~/.twister

cd ~/.twister

git clone [https://github.com/miguelfreitas/twister-html.git](https://github.com/miguelfreitas/twister-html.git) html




