---
layout: post
title:  "Using Boundary Anchors in RegEx"
date:   2017-03-08 08:18:00 +0000
---


I recently finished the lessons on RegEx. It seemed pretty straight forward, but once I started the lab I quickly discovered it's complexities. I got stuck on the first test, but once I learned about border anchors, I was able to get through the rest of the tests fairly easily. 

Three out of the five methods we were asked to build in the RegEx lab involved identifying a starting character, an ending character, and/or a specific length of characters. Through some googling, I found something on border anchors (`\b` and `b/`). This is exactly what I needed to complete those 3 methods. 

By placing `\b` *before* the characters that are getting matched, we are specifying that those characters need to be at the *beginning* of the word to be considered a match. By placing `b/` *after* the charaters getting matched, we are specifying that we are matching those characters at the *end* of the word.

One important thing to note is that `\b` and `b/` is *not* the same as `\B` and `B/`. `\B` and `B/` will actually do the exact opposite of `\b` and `b/`, making sure the following or preceding characters are *not* at the beginning or end of the word. 
