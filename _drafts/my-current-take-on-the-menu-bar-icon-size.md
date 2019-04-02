---
layout: post
title: My current take on the menu bar icon size
tags: ''
date: 2019-04-02 11:00:00 +0200

---
As far as I know, there's _still_ no Apple documentation on the `NSStatusBar` icon size. There are [a few](https://alastairs-place.net/blog/2013/07/23/nsstatusitem-what-size-should-your-icon-be/) [resources](https://www.soydemac.com/denied-nos-permite-evitar-las-canciones-o-cantantes-que-menos-nos-gustan-de-spotify-y-apple-music/) [and discussions](https://discussions.apple.com/thread/7729008) that mostly seem to agree on a few things:

* The width is up to you.
* The icon's max height is 22 pixels.
* If the icon is smaller than 22 pixels, it will be vertically centered.

The choice is then between setting your image's canvas at 22px and placing the icon where you want it, leaving transparent space at the edges, or using the actual size of the icon.

I tried both with a , as you can see in the image below.