---
layout: post
title: "How to Embed YouTube or Spotify on a GitHub Pages Blog"
date: 2018-11-09 14:45:00 -0500
tags: [post]
---

As I've been piecing this place together and learning how Jekyll works, I realized I could not figure out how to embed media from across the web, mainly YouTube videos or Spotify songs, albums, and playlists. After a bit of fiddling, I figured out the easiest way was to create standalone files in the _includes folder and then call an include tag on a post when I need to embed something.

First, create a file named youtubePlayer.html in the _includes folder and put this code in there:

```html
<iframe src="https://www.youtube.com/embed/{% raw %}{{ include.id }}{% endraw %}" 
    width="560" 
    height="315"
    frameborder="0" 
    allowfullscreen>
</iframe>
```

And then in a post, you do something like this:
```
{% raw %}
{% include youtubePlayer.html id=page.youtubeId %}
{% endraw %}
```

With the above syntax, include "youtubeid: ###" in the frontmatter of your post, as that's where it would pull the variable from. You could also just hardcode the youtube video's id into the above code snippet like this:

```
{% raw %}
{% include youtubePlayer.html id="4EU7vvSvV-0" %}
{% endraw %}
```

For a Spotify embed, it's similar, but will have to break out based on what you're sharing. There's a difference in the html between sharing a song, album, or playlist and each would require their own setup. I have mine as three different files in _includes: spotifyAlbumPlayer.html, spotifySongPlayer.html, and spotifyPlaylist.html. Here's what they look like:

YouTube Video:
{% include youtubePlayer.html id="4EU7vvSvV-0" %}

Spotify Album:
{% include spotifyAlbumPlayer.html id="spotify%3Aalbum%3A3BiM8prxKzqm3wERpy9Fvn" %}