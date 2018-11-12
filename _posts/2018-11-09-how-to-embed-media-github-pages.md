---
layout: post
title: "How to Embed YouTube and Spotify on a GitHub Pages Blog"
date: 2018-11-09 14:45:00 -0500
tags: [post]
---

As I've been piecing this place together and learning how Jekyll works, I realized I could not figure out how to embed media from across the web, mainly YouTube videos and Spotify songs, albums, or playlists. After a bit of fiddling, I figured out the easiest way was to create standalone files in the _includes folder and then call an include tag on a post when I need to embed something. Here's how to do it:

### YouTube
First, create a file named youtubePlayer.html in the _includes folder and put this code in there:

```html
<iframe src="https://www.youtube.com/embed/{% raw %}{{ include.id }}{% endraw %}" 
    width="560" 
    height="315"
    frameborder="0" 
    allowfullscreen>
</iframe>
```

When you make a post and want to include the embed, call this in your markdown file:
```
{% raw %}
{% include youtubePlayer.html id=page.youtubeId %}
{% endraw %}
```

With the above syntax, include "youtubeId: $foo," where $foo is the youtube video's id, in the frontmatter of your post. You can hardcode the youtube video's id into the snippet like this:

```
{% raw %}
{% include youtubePlayer.html id="4EU7vvSvV-0" %}
{% endraw %}
```
I plan to do it the second way. Here's an example of it in action:

{% include youtubePlayer.html id="4EU7vvSvV-0" %}


#### Extra Credit CSS
The above will get you rolling, but I would recommend one more thing: wrap your youtubePlayer.html document in a <div> with a class name (I called mine embed-youtube) and give it this CSS so that the video will properly scale with the device:

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

### Spotify
This operates on the same principles as above, but is a little more complicated because of the different types of media you can share and how that changes the URL. I broke this out into three separate files: one for sharing songs, one for albums, and one for playlists each called spotifySong.html, spotifyAlbum.html, and spotifyPlaylist.html, respectively. You'll also need to include the CSS I provide below. It's needed to solidfy the embeds to look right, so don't skip it. 

In each of the files, put the following:

spotifySong.html
```html
<div class="embed-spotify-song">
    <iframe src="https://open.spotify.com/embed/track/{{ include.id }}"  
        frameborder="0" 
        allowtransparency="true" 
        allow="encrypted-media">
    </iframe>
</div>
```

spotifyAlbum.html
```html
<div class="embed-spotify-list">
    <iframe src="https://open.spotify.com/embed/album/{{ include.id }}" 
        frameborder="0" 
        allowtransparency="true" 
        allow="encrypted-media">
    </iframe>
</div>
```

spotifyPlaylist.html
```html
<div class="embed-spotify-list">
    <iframe src="https://open.spotify.com/embed/user/spotify/playlist/{{ include.id }}" 
        frameborder="0" 
        allowtransparency="true" 
        allow="encrypted-media">
    </iframe>
</div>
```

The main difference here is the source URL, which splits out what you're embedding. Once you have this set up, like the YouTube link above, you'll use something like the following in the post you want to embed a Spotify link into:

```
{% raw %}
{% include spotifySong.html id=page.spotifyId %}
{% endraw %}
```

And again, like the above, you'll need to include "spotifyId: ###" in the frontmatter if you use the syntax above or hardcode it and do this:

```
{% raw %}
{% include spotifySong.html id="3V9Ndh1badVfBXnv3niDgE" %}
{% endraw %}
```

Here is what they look like:

Song:
{% include spotifySong.html id="4IFGbY5w97f6FvZNqNfsYb" %}

Album:

{% include spotifyAlbum.html id="3BiM8prxKzqm3wERpy9Fvn" %}

Playlist:

{% include spotifyPlaylist.html id="3V9Ndh1badVfBXnv3niDgE" %}


Now, for the CSS. Unlike the YouTube embed, this provides core functionality for the embed to display properly, so be sure to include this.

```
.embed-spotify-song {
  width: 300px;
  height: 80px;
  position: relative;
  max-width: 100%;
}

.embed-spotify-song iframe, .embed-spotify object, .embed-spotify embed {
  position: absolute;
  width: 300px;
  height: 80px;
  top: 0;
  left: 0;
  max-width: 100%;
}

.embed-spotify-list {
  width: 300px;
  height: 310px;
  position: relative;
  max-width: 100%;
}

.embed-spotify-list iframe, .embed-spotify object, .embed-spotify embed {
  position: absolute;
  width: 300px;
  height: 310px;
  top: 0;
  left: 0;
  max-width: 100%;
}
```

You can tweak the width/height to your liking, but I selected ones that I thought looked best and then used max-width to make sure there was no overflow. You could also use "margin: auto;" to center them if you'd like. With all that out of the way, you should now be able to embed videos and music with no problem going forward.