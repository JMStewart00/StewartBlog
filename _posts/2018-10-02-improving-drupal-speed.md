---
layout: post
title:  "Improving Drupal's Speed"
date:   2018-10-02 12:00:00 -0400
categories: jekyll update
---

One week after the launch of the first really extensive Drupal site I set out to find out what I could do to make the overall experience better for the end user. I wanted to know what I could do to speed things up. So I went searching. Although, right off the bat things were already noticeably faster.

##### Twig debugging and disabling cache for local development.

When developing these Drupal projects I work on, it's easy to get used to the twig debugging being on and cache being disabled and just automatically understanding that it takes FOREVER to reload a change. It's part of the development process for me at this point. But- it was noticeably faster for the dev and production sites with these things turned off. Just pointing this out for anyone leaving them on (mistakenly) on live environments. These should be configured in your development.services.yml file and not your services.yml file.

But back to the heavy lifting, and the real tips and tricks I compiled from across the web to help speed up your Drupal sites.

1. Minimalist Design

This is the number one thing I cam across while I was researching the topic. It's easy to want to go big and extravagant but in reality the minimalist approach is clean and modern, and moreso, familiar with people on the web these days. The trade-off, though, in this strategy is that your site will be without many of the bells and whistles you may want to add.

Because there is so much you can add to Drupal, it can be difficult to slim it down. However, everything from engaging modules to alluring themes can affect the performance of the website.

By sticking with fewer graphics and calls to the database, the site can deliver a much faster experience to the visitor.

2. Image Optimization

Image use is important when accompanying any piece of content. For instance, did you know that blogs get 94% more views if there is imagery in the post? However, these images are a double-edged blade.

While they can help engage the audience, they can also hinder Drupal performance.

I see extremely large graphics all the time on websites that are slower than others. This is especially true when someone uses a picture directly from his or her phone to use on the site.

The easiest way to optimize the images is to make them the right size prior to upload. Don’t use huge graphics and then try to make them fit by altering the size using code.

Browsers will still render the entire graphic as a whole. Keep images to 72dpi and upload the size you need.

Using image styles to crop and resize images in Drupal is a great way to limit size as well.

3. Minimize the Modules You Use

If you don’t want to go with a minimalist approach to web design, consider keeping modules to a minimum. Each addition to Drupal 8 will take away from its speed. This is because each one will have code that needs to run or calls to a database.

Keeping module use low also includes uninstalling those you are not using. By keeping as much off of the system as possible, you make the website much “lighter” and easier for browsers to operate.

Even if the module is not currently active, it’s still safe to assume that it’s affecting performance.

4. Caching Modules

Caching is an excellent way to save speed on a website. This is when elements of the site are essentially saved and used when someone visits. It’s like saving the settings on a program you use on a regular basis.

The downside to this is when people empty their own cache on the computer. Back in the day, I used to empty my cache on a regular basis to help improve computer performance. However, this isn’t as much of an issue today.

There are some built-in methods to enable Drupal 8 to do this without installing additional modules. However, some extensions simply have greater control and versatility than the included methods.

For example, the Boost module will cache and compress coding. This allows the site to perform at peak levels regardless if the user is anonymous or authenticated.

It also adjusts the life cycles of different caches for the data which improves the visitor experience as well as SEO.

5. Use a Content Delivery Network

One of the easiest ways to boost speed is through the use of a Content Delivery Network, or CDN. This is exceptionally useful as it doesn’t require that much effort from yourself to make the site faster. The process is automatic on most hosting providers today.

A CDN distributes your website across a network of servers in various locations. These copies are useful when someone tries to access your website.

For example, a visitor from Miami may access your CDN site from a server in Atlanta instead of the one in Los Angeles. This increases speed by removing distance as a factor.

6. Update Your Version of PHP

PHP is the backbone of many content management systems like Drupal. Each version has potential to improve performance. Making sure your website is using the most current stable version improves the experience for everyone.

However, you want to be careful about changing versions of your software. Some modules or scripts may not support certain versions of PHP.

I’ve come across a few plugins that absolutely refused to work with older versions of PHP. I’ve also seen a few older ones have problems with the newest version as well.

Recently, Drupal has bumped support to using strictly the newest version of PHP at 7.2. It's said to be much faster than the previous version at 5.6 or even 7.0.


7. Be Selective of the Background Image

Images within content are not the only graphics to worry about. Many people like to use fancy or high-resolution imagery in the background. Depending on the size of the file, this will affect performance.

If at all possible, you should try to keep the background of your Drupal 8 site to basic color schemes.

Many templates will allow you to adjust the background image in Drupal. By dropping the graphic and using hexadecimal color platforms, you take out a large component that browsers don’t have to render upon visiting.

If you still want to use a large JPG file, make sure you save it at a lower quality. It will still look nice while keeping the file smaller than the original.

8. Use Lazy Loading

Lazy loading is when elements of a website are only accessed as needed. On a traditional website, all the images and content are pre-loaded into a web browser when someone accesses the site.

This happens whether a person actually views the material or not. With lazy loading, those elements are loaded as soon as a user scrolls to view the content.

The use of lazy loading can also be used in a mobile environment. Considering there were 237.5 million mobile phone Internet users in the United States in 2017, improving mobile speed is a crucial part of performance.

Installing modules such as Blazy will help your Drupal 8 site engage some of those users.

9. Expire Your Headers

I've never actually used this but it seemed to pop up all over the place so I'm including this as an important trick to helping speed up your site.

Expiring headers is a bit trickier than other tips in this list. However, it has potential to make caching more efficient on the browser’s end of the website.

What expiring headers does is tell the visitor’s web browser to save certain elements of the site which don’t often change. Things like backgrounds, icon images, logos and more are stored in this fashion.

As a result, the user’s computer simply recalls the graphic itself the next time that person visits your site.

10. Manage the Use of CSS and JavaScript

Using CSS and JavaScript on a website is common practice as it offers excellent methods for customization and flexibility. However, your site can be affected by too much of a good thing.

Keep your coding to a minimum and try to avoid excessive CSS file and JavaScript use. These two can easily reduce performance.

In Drupal 8, there is a built-in ability to aggregate these extra files into one to help reduce load time. However, many prefer to use the ADVAGG module to aggregate CSS and JavaScript to boost speed.

11. Fast Load 404 Errors

No one likes the idea of something on his or her website breaking to cause a 404 error. When this happens, it can be exceptionally slow. Even a failed image can cause the system to lose performance.

Improving how these errors are handled by the system can help improve the site’s ability to function.

Although Drupal 8 has limited ability to handle 404 errors in a fast and efficient manner, you can always install the Fast 404 module. This not only allows the site to utilize resources better, but it also allows you to whitelist files and check pathways of the problem.