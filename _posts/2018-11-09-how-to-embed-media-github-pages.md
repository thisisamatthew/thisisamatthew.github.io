---
layout: post
title: "How to Embed YouTube or Spotify on a GitHub Pages Blog"
date: 2018-11-09 14:45:00 -0500
tags: [post]
---

As I've been piecing this place together and learning how Jekyll works, I realized I could not figure out how to embed media from across the web, mainly YouTube videos or Spotify songs. After a bit of fiddling, I figured out the easiest way was to create standalone files in the _includes folder and then call that on a post when I need to embed something. It looks like this:

Create a file called youtubePlayer.html in the _includes folder and put this code in there:
```html
<iframe src="https://www.youtube.com/embed/{{ include.id }}" 
    width="560" 
    height="315"
    frameborder="0" 
    allowfullscreen>
</iframe>
```

And then in a post, you do something like this:
```html
{% include youtubePlayer.html id=page.youtubeId %}
```

If you use page.youtubeId, be sure to include youtubeid in the frontmatter of your post, as that's where it would come from. You could also just hardcode the youtube video's id into that code. It would look something like this:

```html
{% include youtubePlayer.html id=4EU7vvSvV-0 %}
```

Examples:

Youtube Video:
{% include youtubePlayer.html id=4EU7vvSvV-0 %}

