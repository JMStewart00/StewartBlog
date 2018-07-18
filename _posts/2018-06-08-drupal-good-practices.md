---
layout: post
title:  "Architectural Mistakes not to make in Drupal"
date:   2018-06-20 12:00:00 -0400
categories: jekyll update
---

*Many pieces of this blog post have been taken from other sources and will serve as a reference for my future self as a place to come to reference details on Composer and Drupal. All it ever takes is a little mashing at the keyboard and lots of dependency errors for you to really nail down how Drupal and Composer can work together.*

It's been seven months since I ventured into a Drupal turorial for the first time and along the way I've had my fair share of ups and downs with the project. It's powerful. And frustrating. But here's a few things I've picked up along the way. 

## CONFIG IS A SINGLE SOURCE OF TRUTH
Be sure you always update config files. Pull down before starting your work. Import into your local environment before starting. Just always be sure you're working with the latest and greatest config setup for your site. You don't want to lose anything someone, or yourself, has done to get there. It's important you know whether in, or out, config importing/exporting is considered the single source of truth. Bye bye config. 

## NEVER HACK CORE (OR CONTRIB)
Don't change the framework. Instead, write your own code as a module. Pantheon, doesn't follow this rule, and it creates a lot of extra work for them. But, they have an entire company of developers to maintain their fork of Drupal. The rest of us should stick to the official release. This is true no matter the framework you're in. If you hack WordPress, your project will fail during automatic updates!

## USE CONFIGURATION BEFORE CODE
Instead of hard coding a class or a snippet of logic into a theme, set these values in configuration and then apply the configuration with code. This allows your code to change in the future without being rewritten. This also leads us to choose high quality, well maintained modules to build our sites out of. Reusing code is one of the most basic steps in writing quality software because reusable code will have fewer bugs and more features.

Instead of writing a massive "glue" module, break up functionality into reusable modules and use configuration to apply advanced functionality so that each module is more powerful and easier to modify without rewriting the code.

## YOUR CUSTOM MODULES
Drupal.org only talks about contributed modules, but this too many modules advice holds for custom modules as well. The more custom modules you write, the more work it takes to maintain and modify your website. Instead of writing a large collection of custom modules, or a single giant glue module, consider publishing your modules on Github. This will encourage you to create reusable code that has configuration needed to make them reusable and future proof.




There's plenty more that I could include but this is a good start...
