---
layout: post
title: Track where someone downloaded your Mac app
tags:
- analytics
- apps
- osx
- programming
- indie
- xcode
date: '2016-05-03 11:37:00'
---

Figuring out what works and especially what doesn't is a big part of building products. Whether you're trying to figure out which feature to build or where to spend money on marketing, analytics can help you make those decisions.

If you're building a web platform it's relatively easy to setup Google Analytics (or something similar) to track a user's behavior from the moment they hit your site until they decide to purchase your product. 

If you're building desktop apps, things get a little more complicated.

Through some experimenting and digging around in how OS X handles downloads, I've come up with a way to connect how a user hits your product's site with the moment they open the app. This is incredibly useful.

By connecting the pre and post download path of a user you'll be able to tell if a potential customer came to your site through that post on Facebook or that email campaign you sent out last week. All you have to do is append a ```?ref/source/whatever=[name of your campaign]``` identifier to your download URL and then read that identifier from OS X' QuarantineEventsV2 database.

That sounds a lot more complicated than it is. I've put [a sample project](https://github.com/boyvanamstel/Where-From-Quarantine-Edition) on GitHub that shows how this works technically.

![A few lines of code to read the contents of QuarantineEventsV2](/assets/blog/Screen_Shot_2016-05-03_at_11.34.12-web.jpg)

## Full use case

Let's say we're building a Mac app and we just ran a marketing campaign through Facebook and send out a news letter. We've setup analytics in our Mac app in such a way that we can track app opens and some buttons clicks–the 'Buy Now' button specifically. We use specific landing pages (or URL parameters) that link to our website from the Facebook post and news letter.

The Facebook campaign and news letter link to the homepage, but both append some parameters to the URL: https://example.com/?source=facebook-campaign and https://example.com/?source=news-letter respectively.

We've setup our site and web server to 'forward' the ```?source=``` parameter to the download URL. This means instead of just https://download.example.com/app.zip, the app's download URL becomes https://download.example.com/app.zip?source=facebook-campaign (or ?source=news-letter).

Our app includes the code from the sample app, so we can retrieve the URL that was used to download the app. We can now do this:

1. Mister X receives our news letter and clicks through to our website.
1. Mister X likes what he sees and clicks the download button.
1. Mister X launches the app.
1. Mister X clicks around and uses the trial version of the app.
1. After a few days Mister X buys the app.

Because the app registered where the app was downloaded, we know which campaign caused Mister X to download and ultimately buy the app. By comparing several downloads we should be able to determine which source was the most successful.

I would love to hear your thoughts on this approach. Let me know on Twitter: [@boyvanamstel](https://www.twitter.com/boyvanamstel).
