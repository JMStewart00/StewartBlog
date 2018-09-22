---
layout: post
title:  "Merge Conflicts in your Composer Files"
date:   2018-09-22 12:00:00 -0400
categories: jekyll update
---

You're working on a project, an urgent bug comes up so you switch your git branches, make the fix, get it reviewed and merge it into the source code. You're feeling like a million bucks for saving the day. Meanwhile the feature you've been working on in another branch for the last three weeks is ready for your attention again and you have to get the work you did on the urgent request to sync up with the work you've done over the past few weeks.

Or your team made a ton of changes that have been pushed to live and you need to sync that up with your current branch as well.

I know we've all been here:

```
CONFLICT (content): Merge conflict in composer.lock
Automatic merge failed; fix conflicts and then commit the result.
```

Don’t panic, breathe, let’s walk through this.

Since I joined Apax last year, I have been working on teams of varying sizes but all with composer managed Drupal 8 projects. With more people involved in the process of working with composer, adding, updating and removing drupal modules and PHP libraries, merge conflicts are bound to happen. Ideally I would tell you to leave that process to only one person, but that is not realistic in teams over, well, one person.

So it's bound to happen, but how do we keep our sanity and not break a keyboard or waste endless time figuring out what to do.

### What I DONT do.
While reading other blog posts on this I found a practice that I consider not ideal. In most blogposts the first step towards fixing the conflict is usually:

```
$ git merge --ours composer.lock
```

What does this do? This will impose your version of the lock file, which seems fine, but has a catch. The catch here is that by ignoring the remote lock file you are discarding any updates done by the other developer. You may have just rewrote everything already done.

### What I DO do.
Its a simple switch around.

First I get the other developer's changes by checkout out their file from git:

```
$ git checkout origin/{base} -- composer.lock composer.json
```
Then, since you already know what has changed on your branch, you replay your changes on top of this, like:

```
$ composer require {new/package} --update-with-dependencies
$ composer update {existing/package}
```

You should know exactly what changes you made, so this should be no problem. Now you have kept all non-conflicting changes and updates from the other developer and applied your changes on top of it and the state of your dependencies is predictable and stable.

It's not exactly a git-friendly way of doing this, but it'll save you plenty of headaches.