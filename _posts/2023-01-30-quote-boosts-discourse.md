---
layout: post
title: "A Brief Take on the Quote Boost Discourse"
date: 2023-01-30 08:00:00 -0500
tags: post blog
---
With the big migration to Mastodon, one of the big differences is that Mastodon currently has no official "quote retweet" functionality (in Mastodon terms, this is called a boost, so I will henceforth call these quote boots) This has caused a lot of discourse on the site. Some reasonable, some not, but I thought I'd throw my hat in the ring with a particular view I don't think I've seen on the matter. 

I'm in favor of adding a quote function, but I want to see a very specific piece of functionality as part of the implementation and I'm not even sure how feasible it is: **original posters should have the ability to disable click-through to their post from a quote post**. 

I see this as solving what I see as one of the main concerns brought forth against implementing quote boosting: it leads to harassment when someone is quoted by someone bigger and their followers click through and attack them. If posters can turn off the click-through, people can be quoted, preserving authenticity that something has been quoted, while also providing a way to slow harassment by people with fast access to click through and say something horrible. I understand this doesn't stop someone from going and manually finding the original post, but I think it empowers people to limit the speed at which someone can get to them and I think helpful deterrence is a good idea, even if imperfect.

When it comes to implementation, I'm at a bit of a loss if this would be possible. I don't know the Mastodon API well enough to speak to it directly, but I imagine there could be some post-level option for 'no clickthrough' that then clients could respect when implementing an official quote boost functionality. Right now, I'm assuming apps like Ice Cubes are basically just injecting an iframe and parsing the text of a linked mastodon post to show them, but an official API implementation could give clients parameters that could stop a quote boost from being clickable if the server flags that functionality. Obviously more thought would need put into this by people smarter than me, but I'd love to see it considered or as a starting point for some other implementation detail to help original posters stem the bleed of possible harassers via quote boost.