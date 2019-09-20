---
layout: post
title: "My Git Cheat Sheet"
date: 2019-09-20 15:50:00 -0500
tags: post blog

---

I've been using and learning git a bunch lady, so I started jotting down some of the basics I found myself using often and wanting to make sure I remembered and left a note in the plainest language possible about what it does. Figured it'd be worth putting out there. I'll probably add a few more as I find myself in recurring situations.

**git remote update**

* update all branches references with remote ones. No merge. More all-encompassing than git fetch, which only updates the branch you're on. Good place to start if you want to make sure your local git knows what's happened on the server.

**git add .;git commit -m 'message header' -m 'message body';git push**

* all on one line will add any tracked or untracked files, commit them with the message with -m and then push them up to the server. Second -m can be cut if you have no message body text you care to put in the commit.

**git commit -am 'message text';git push**

* Like the above, except for when you haven't added any new files. Good for quick updates.

**git clean -dfx**

* nuke everything that's untracked. good use in conjunction with "git reset --hard branchName" to make a branch up to date with remote and just say goodbye to whatever you had locally. I find this useful when it's been a while since I've pulled something down and know I don't care about whatever I last had locally.

**git checkout -b branchName**

* Will create a new branch of branchName and move you into that branch

**git branch -d branchName**

* Delete a branch

**git stash apply stash@{#}**

* apply the stash to your current branch. If you don't specify a stash, it will assume the most recent.

**git log \-\-oneline \-\-decorate \-\-graph \-\-all**

* Show your commits, but pretty

**git config --global --edit**

* open your .gitconfig file in yoru C:\users\user folder in a text editor so you can see and update all your config settings. If you append --local instead of --global, it will open the config file for the specific branch you're in.