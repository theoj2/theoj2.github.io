---
author: tjones
comments: false
date: 2013-12-22 21:28:50+00:00
layout: post
slug: linux-booting-blank-screen-2
title: Linux Booting to Blank Screen
wordpress_id: 1061
categories:
- old
tags:
- Old
---

On my laptop I've encountered an issue where Linux would would boot to a blank screen. I found that my issue related to the display backlight control. I found that adding either of the following two kernel parameters would fix the issue.   

_acpi_backlight=vendor   

nomodeset_





Try acpi_backlight=vendor first because nomodeset disables 3d acceleration.
