---
layout: post
title: "How to Embed YouTube on a GitHub Pages Blog"
date: 2018-11-09 14:45:00 -0500
tags: [post]
---

As I've been piecing this place together and learning how Jekyll works, I realized I could not figure out how to embed media from across the web, mainly YouTube videos. After a bit of fiddling, I figured out the easiest way was to create standalone files in the _includes folder and then call an include tag on a post when I need to embed something.

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

With the above syntax, include "youtubeId: ###" in the frontmatter of your post, as that's where it would pull the variable from. You could also just hardcode the youtube video's id into the above code snippet like this:

```
{% raw %}
{% include youtubePlayer.html id="4EU7vvSvV-0" %}
{% endraw %}
```

### Example
{% include youtubePlayer.html id="4EU7vvSvV-0" %}


### Extra Credit CSS

The above will get you rolling, but I would recommend one more thing: wrap your youtubePlay.html document in a <div> with a class name (I called mine embed-youtube) and give it this CSS so that the video will properly scale with the device:

```css
.embed-youtube {
    position: relative;
    padding-bottom: 56.25%;
    padding-top: 25px;
    height: 0;
  }

.embed-youtube iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
```

## Spotify

{% include spotifySong.html id="4IFGbY5w97f6FvZNqNfsYb" %}

and now an album:

{% include spotifyAlbum.html id="3BiM8prxKzqm3wERpy9Fvn" %}