---
layout: post
title: My current take on the NSStatusBar icon size
tags:
- xcode
- macos
- design
date: 2019-04-02 11:00:00 +0200

---
As far as I know, there's still no official Apple documentation on the `NSStatusBar` icon size. There are [a few](https://alastairs-place.net/blog/2013/07/23/nsstatusitem-what-size-should-your-icon-be/) [resources](https://www.soydemac.com/denied-nos-permite-evitar-las-canciones-o-cantantes-que-menos-nos-gustan-de-spotify-y-apple-music/) [and discussions](https://discussions.apple.com/thread/7729008) that mostly seem to agree on a few things:

* The width is up to you.
* The icon's max height is 22 pixels.
* If the icon is smaller than 22 pixels, it will be vertically centered.

The choice is between setting your image's canvas at 22px and placing the icon where you want it (leaving transparent space at the edges) or using the actual size of the icon.

I tried both as you can see in the image below. Focus on the two icons in the center that represent a radar. Do you have a preference?

![A screenshot of the menu bar with two custom icons set next to each other](/assets/blog/menubar-icons-size.jpg)

The one on the left is an image 22px high with the 16x16px icon centered inside. The right one is just the square icon. They appear very similar and are shown at the exact same size.

It's very hard to see, but sitting in my menu bar I prefer the one on the right (just the 16x16px icon) centered by the operating system. It seems a little sharper to me. No hard evidence though. It could be the odd rotation of the left icon.

As for the width, the left one has 1px of padding left and right. The right one has no padding at all. Sitting next to the WiFi indicator, it might not be a bad idea to give it some more breathing room.

As the icon is square, I can just use a square `NSStatusItem` length. This sets the status item width to be equal to the height of the menu bar, thus 22 pixels.

``` swift
let statusItem = NSStatusBar.system.statusItem(withLength: NSStatusItem.squareLength)
```

And there we go. If the icon wasn't square or would look better with its width set manually, I could use `.variableLength` like I did in the previous screenshot and adjust the width in the image.

![A screenshot of the menu bar with the custom icon looking like it should](/assets/blog/menubar-icons-size-square.png)