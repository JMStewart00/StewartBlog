---
layout: post
title:  "My Drupal Adventure...so far."
date:   2018-09-02 12:00:00 -0400
categories: jekyll update
---

Becoming a developer was daunting. I dabbled in some behind the scenes code work as a Sports Information Director. I could use tags, look at source code and get the page to do what I wanted with my limited knowledge. I managed some Squarespace pages but I was stuck in the realm of only doing what the GUI would allow me to do. So I took the Awesome Inc U Bootcamp to completely change my life.

It's been almost a year to the day I started working at APAX Software in Lexington. Nothing has been so frustrating and challenging or rewarding and instrumental as diving into Drupal 8 as the in-house Drupal-guy.

## Humble Beginnings

I wasn't very familiar with CMS options for web development. I was fully into being a Pyhton/Django backend, with a React-Redux frontend developer. I enjoyed functional Javscript programming. I could run with anything and at least Google my way to a solution. It was fun.

Then I got my first Drupal assignment. No one in the office had the experience so I couldn't run to one of the senior devs to get me out of the hole I had dug. Our client didn't have an in-house developer any more; in fact, the whole project hadn't been touched in four or five months, Drupal had gone from 8.3 to 8.5 in that time and the local dev process went from Kalabox to Lando (same product just a different name). So I was up a creek as they say. And there was a hole in the boat.

I spent two weeks doing Drupal tutorials. I was a master at creating Drupal projects from scratch. I read everything I could find. Whether I understood it or not I still read it, sometimes twice.

It took those first two weeks plus another to spin up that first Drupal project locally. It took another three weeks to navigate through the extremely frustrating Drupal core upgrades that have been plagueing a lot of people as Drupal upgraded their Symfony and Drush requirements in the 8.5 minor release.

I got it to work though, finally, and I don't even know what it took to do it.

## No two projects are alike

Since that first project got off the ground and I looked like I was looking for a needle in a haystack in a dark cave, I've actually been one of the sole developers on three very different Drupal 8 projects.

In one instance we host Drupal on Pantheon and develop locally with Lando (which is super easy in my opinion, at least at this point). Another is totally a making of our own, and we developed it from the ground up. We use VagrantBox and have integrated React-Redux into the project. Super fun! And thirdly we have an Acquia Cloud client that utlizes a Jenkins build to deploy code changes on Github.

Because my understanding of Drupal was so rudimentary the differences in each made life as frustrating as it could be. What worked on one may not have been the course of action for another. Getting each one to a stable and secure point of Drupal at at least 8.5.1 was different and because of that my understanding of Drupal, the love I now have for Drupal's commitment to being Composer managed, and the comfort I have with the framework is incredible. It made me understand the framework at a less shallow level.

## Drupal: Now where do I go?

As a seasoned, year-of-experience developer where do I need to go from here with Drupal. It seems it's here to stay for me and, as with anything I do, I want to only be the best I can be at it. So where do I go now?

Well, lately, and hopefully I'll write a blog post about it soon, I've been trying to be better at debugging and also setting up PHPUnit for unit testing.

I switched my IDE to VSCode and set up XDebug and it's been super handy. I want to make the jump to PHPStorm but I can't seem to pay for that just yet.

I set up two basic unit tests on a project about two weeks ago and that seems to be a relevant next step. So what else?
1. Clean up content creations and reusable components
  - I know from all of my React experience that creating components that can be used in different places that allow you to DRY code is best practice. I want to use the Paragraphs module to help do that. Maybe try my hand at a "Call to Action" component or something.
  - Keep it simple and create better relational data/content types.
  - create reusable fields to cut down on that.
2. Dive into the core code and learn more about the way object-oriented programming works with PHP. I'm still so unsure of what that looks like or even means.
3. Headless Drupal for a React-Redux front end?
4. More robust custom modules?
5. Interact and understand the Drupal API structure better.

There's so much to learn and even though I've been developing Drupal projects for the last 7 months I know I've only scratched the surface.
