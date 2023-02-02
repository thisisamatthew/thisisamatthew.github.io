---
layout: post
title: "Moving Task Management Into Obsidian"
date: 2023-02-01 20:30:00 -0500
tags: post blog
---
I love markdown, I love plain text files, and I love Obsidian. I went all-in on the application for my personal notes long ago, but I finally made the switch at work and figured I'd drop a quick write up on how I'm using the app to handle task management. 

Even before I used Obsidian, I used a "Daily Note"-like concept at work. I used to be in OneNote and would just manually make a new one each day, but now I use the [Periodic Notes](https://github.com/liamcain/obsidian-periodic-notes) plugin. With this installed, when I start my day, I click the shortcut in my sidebar and it pops up with that day's new note with that day's template ready for me to fill out. I'll go over daily note template some other time, but it's important to know that the daily note is the hub to pretty much everything I do in Obsidian. Everything sprawls out from there, including my task management.

So onto tasks. I use the [Tasks plugin](https://github.com/obsidian-tasks-group/obsidian-tasks) and throughout the day, any time a new task comes up, I chuck it into my daily note. Because Tasks allows you to query against your entire vault, I then use a Task Dashboard note that is able to easily collect any number of tasks from across all of my notes. My task management needs at work aren't insane, but I've found this useful so that I can focus on the day-to-day while then being able to quickly and easily pull together any information from across a multitude of notes. On my task dashboard, I have a handful of basic queries setup. Here's what they are:

### Due Today
~~~
```tasks
not done
due today
```
~~~

### Due This Week
~~~
```tasks
not done
(due after sunday) AND (due before next sunday)
```
~~~

### No Due Date
~~~
```tasks
not done
no due date
path does not include <relevant folder path here>
```
~~~

I use this one for as a catch-all for anything I didn't give a due date to ensure nothing gets lost in the cracks. Item of note here is that you'll see me use the `path does not include <relevant folder path here>` several times. I'm using this to exclude my templates folder, which have empty tasks set up in them so that I don't end up with a bunch of loose tasks hanging out in these filters. You can use this syntax to exclude (or only include!) a particular file or folder.

### All Tasks
~~~
```tasks
not done
path does not include <relevant folder path here>
```
~~~
This one gives me *everything*. I like having this for reference. As my tasks grow, I'll see if this is ever useful, but it gives me a sense of security to be able to glance at it.

### Recently Completed
~~~
```tasks
done
limit 20
```
~~~
This just shows me the 20 most recent done tasks.

And that's it! It's pretty simple right now, but it's getting the job done. One last closing point is that I also use a css style to change the way page links were rendered for tasks, which I pulled from the ["How to Style Backlinks"](https://obsidian-tasks-group.github.io/obsidian-tasks/how-to/style-backlinks/) page on their documentation. Here's that code block:
```css
li.plugin-tasks-list-item > span.tasks-backlink > a {
    content: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 36 36'%3E%3Cpath fill='%238899A6' d='M15 9l6-6s6-6 12 0 0 12 0 12l-8 8s-6 6-12 0c-1.125-1.125-1.822-2.62-1.822-2.62l3.353-3.348S14.396 18.396 16 20c0 0 3 3 6 0l8-8s3-3 0-6-6 0-6 0l-3.729 3.729s-1.854-1.521-5.646-.354L15 9z'/%3E%3Cpath fill='%238899A6' d='M20.845 27l-6 6s-6 6-12 0 0-12 0-12l8-8s6-6 12 0c1.125 1.125 1.822 2.62 1.822 2.62l-3.354 3.349s.135-1.365-1.469-2.969c0 0-3-3-6 0l-8 8s-3 3 0 6 6 0 6 0l3.729-3.729s1.854 1.521 5.646.354l-.374.375z'/%3E%3C/svg%3E");
    height: .9em;
}
```

I do think this workflow works best by committing to the daily note as the hub, so that's really my main recommendation here. I think of it like this: work happens one day at a time and it's good to have a record of things chronologically. Then, the power lies in being able to query against that data in any way I see fit without losing the original, time-bound context in my daily notes. While in my provided example, I'm embedding my tasks into an overall dashboard, I could also quickly set up this query against tasks with a certain tag (say, for a particular work project) and then have a project home page and link to the related meeting notes and tasks on any relevant page, while, again, not losing the original context of the task, meeting, etc among my other work. As usual, the flexibility of markdown combined with simple querying languages is irreplaceable.

As I commit further to this workflow, I'll make a follow-up as my needs evolve, but for now it's covering my bases and I'm losing track of less things on my plate, including exactly what people ask of me and when. Next up, I'll try and cover the templates for my daily note & meetings.