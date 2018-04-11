---
layout: post
title: Updating Internet Explorer RSS Feeds
date: 2008-05-18 23:12
author: spdenne
comments: true
---

I tried out [RikReader](http://11011.net/software/rikreader) recently, which is one of the class of feed readers which
use Internet Explorer's (and Vista's) list of RSS feeds. It has its pro's and con's, but the lack of the ability to
refresh all feeds was initially a surprise.

<!--more-->
 
It doesn't need that feature though, since using IE's feeds, it also uses IE's feed updating mechanism. I don't really
like IE's feed updating mechanism, since it is a background task that keeps using my laptop's resources when it wants
to, rather than when I want it to.
 
Investigating how it updates, I discovered that I can disable the background task, and when I want the feeds updated, I
can run:
 
**`msfeedssync forcesync`**
 
I thought I'd blog about it, since there are currently so few mentions (in English) of this.
 
I created a shortcut to run that on my Quick Launch bar. Can anyone comment on where to find a pre-installed rss icon?

