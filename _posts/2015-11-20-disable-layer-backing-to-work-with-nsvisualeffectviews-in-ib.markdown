---
layout: post
title: Disable layer backing to work with NSVisualEffectViews in IB
tags:
- xcode
- programming
date: '2015-11-20 13:27:00'
---

Found yourself unable to move around (or even freakin' select) elements on a layer backed `NSVisualEffectView`?

Just toggle the Core Animation Layer checkbox in Interface Builder and voilà, all fixed. Oh and everything turns red obviously, because `NSVisualEffectView`s need layer backing.. 👍

![Interface Builder showing a red NSVisualEffectView](/assets/blog/Screen_Shot_2015-12-01_at_13.31.21.png)
