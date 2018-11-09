---
layout: post
title: "How to Embed YouTube or Spotify on a GitHub Pages Blog"
date: 2018-11-09 14:45:00 -0500
tags: [post]
youtubeId: 4EU7vvSvV-0
---

As I've been piecing this place together and learning how Jekyll works, I realized I could not figure out how to embed media from across the web, mainly YouTube videos or Spotify songs. After a bit of fiddling, I figured out the easiest way was to create standalone files in the _includes folder and then call that on a post when I need to embed something. It looks like this:

TESTING STILL JESUS CHRIST WHY WON'T THIS WORK

{% include youtubePlayer.html id=page.youtubeId %}