---
layout: post
title:  "Best Practices: Get the most out of Drupal and do it well."
date:   2018-06-08 12:00:00 -0400
categories: jekyll update
---

This is definitely just acting as a bookmark for me. Acquia, one of the leaders of hosts in Drupal sites, run a very informative blog that is great at giving you little snippets of information that will make you a better Drupal programmer moving forward.

From: [Acquia's Blog on Mistakes](https://dev.acquia.com/blog/5-mistakes-to-avoid-on-your-drupal-website--number-1-architecture/07/06/2016/10646)

Here's the key points!

#Architecture: Content
Content is the essence of your website, the reason it exists. Determining the structure of content is the first
step in creating website architecture.

Best Practice
Plan your content structures, including fields and content types. Clear content architecture helps ensure
good performance, a better user experience, and easier maintenance. You will find overlap here with Display Architecture, because Views often depends on fields available in specific types.


#Architecture: Display
Drupal is a powerful tool for displaying content in different regions, formats, and displays. Display
architecture includes the Views, Panels, and Context modules.

Best Practice
Plan your display architecture to render content only when needed . Optimize and reuse as much as possible. Always separate logic and presentation. Start with a solid base theme and learn it thoroughly. The ease of changing the look and feel of your website is an indication of good display architecture.

#Architecture: Site or Functionality
Site architecture includes how the site works, the number of modules, and how they interact.

Best Practice
Keep your site lean, using the minimal amount of code and fewest number of modules necessary. Use contrib modules whenever possible rather than writing custom code. Become expert at key contrib modules, such as Views and Panels. Follow Drupal standards for custom code. Reevaluate your architecture periodically.
