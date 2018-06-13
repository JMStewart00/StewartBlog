---
layout: post
title:  "Composer and Drupal: Conducting Dependencies Drupal 8 Project "
date:   2018-05-15 12:00:00 -0400
categories: jekyll update
---

*Many pieces of this blog post have been taken from other sources and will serve as a reference for my future self as a place to come to reference details on Composer and Drupal. All it ever takes is a little mashing at the keyboard and lots of dependency errors for you to really nail down how Drupal and Composer can work together.*

My Take
=====

At a basic level, Drupal ships with a starter composer.json file that you can use if you're building simpler Drupal sites to manage modules and other dependencies. 

One thing I've found lacking in my journey towards dependency management nirvana is a list of all the little tips and tricks that make managing a Drupal 8 project entirely via Composer easier. Therefore I'm going to post some of the common (and uncommon) things I've found to be helpful, thing that I do, and keep this list updated over time as best practices evolve or other practices come to fruition.

Adding a new module
-----

From my understanding, in the old days, you would either download a module from Drupal.org directly (up to the newest Drupal 8.5 release), and drag it into your codebase, or, conversely, if you were CLI savvy, you'd fire up Drush and do a `drush dl modulename` then `drush en modulename` to enable it.

But with Composer, and especially with the way many (if not most) Drupal 8 modules integrate with required libraries, it's more correct, now, to use composer require to add a new module.

Drupal.org modules don't quite follow semantic versioning, but the way release versioning works out with the Drupal.org packagist endpoint, you should generally be able to specify a version like "give me any version 8.x-1.0 or later, and I'll be happy".

Therefore, the proper syntax for requiring a module this way (so that when you run composer update drupal/modulename later, it will update to the latest stable 8.x-1.x release) is:

`composer require drupal/modulename:^1.0`
This says "add modulename to my codebase, and download version 1.0 or whatever is the latest release in the 8.x-1.x release series *(including alpha/beta releases, if there hasn't been a stable release yet)*.

Note on version constraints: Two of the most-commonly-used version constraints I see are ~ (tilde) and ^ (caret). Both are similar in that they tell Composer: 'use this version but update to a newer version in the series', but the tilde is a bit more strict in keeping to the same minor release, while the caret allows for any new version up to the next major release. See this article for more details: Tilde and caret version constraints in Composer. See this Drupal core issue for discussion on why the caret is often preferred in Drupal projects: Prefer carat over tilde in composer.json.

Updating modules
-----

Early on in my Composer adventures, I did the reasonable thing to update my site---I ran composer update, waited a while for everything to be updated, then I committed the updated composer.json and composer.lock files and was on my merry way. Unfortunately, doing this is kind of like cleaning a dirty blue dress shirt by washing it in a bucket of bleach---sure, the stain will be removed, but you'll also affect the rest of your shirt!

If you are meticulous about your dependencies, and lock in certain ones that are finicky at specific versions (e.g. composer require drupal/modulename:1.2) or at a specific git commit hash (composer require drupal/modulename:dev-1.x#dfa710e), then composer update is manageable.

**But if you're managing a project with many moving parts using more than a dozen contributed modules... be cautious when considering running composer update without specifying specific modules to update!**

Instead, what I recommend is a more cautious approach:

#####See what modules need updating.
Update those modules specifically using composer update drupal/modulename --with-dependencies.
If you had required the module using a release series like drupal/modulename:^1.0, then Composer will update that module---and only that module---to the latest tagged release in the 8.x-1.x branch. And adding --with-dependencies will ensure that any libraries the module depends on are updated as well (e.g. if you update the Search API Solr module, the Solarium dependency will also be updated).

####Another quick tip
In addition to Drupal core's update module functionality and drush pm-updatestatus, you can use Composer's built-in mechanism to quickly scan for outdated dependencies. Just use `composer outdated`. This will show you if Drupal core, contrib modules, or any other dependencies are outdated.

Removing modules
----
This one is pretty easy. To remove a module you're no longer using (be sure it's uninstalled first!):

`composer remove drupal/modulename`
Older versions of Composer required a flag to also remove module dependencies that aren't otherwise required, but modern versions will remove the module and all it's dependencies from your composer.json, composer.lock, and the local filesystem.

Requiring -dev releases at specific commits
From time to time (especially before modules are stable or have a 1.0 final release), it's necessary to grab a module at a specific Git commit. You can do this pretty simply by specifying the dev-[branch]#[commit-hash] version constraint. For example, to get the Honeypot module at it's latest Git commit (as of the time of this writing):

`composer require drupal/honeypot:dev-1.x#dfa710e`
Be careful doing this, though---if at all possible, try to require a stable version, then if necessary, add a patch or two from the Drupal.org issue queues to get the functionality or fixes you need. Relying on specific dev releases is one way your project's technical debt increases over time, since you can no longer cleanly composer update that module.

Other Tricks
-----

Composer lets you track 'dev dependencies' (using require-dev instead of require) that are installed by default, but can be excluded when building the final deployable codebase (by passing --no-dev when running composer install or composer update).

One concrete example is the inclusion of the Drupal VM codebase in a Drupal project. This VM configuration is intended only for local development, and shouldn't be deployed to production servers. When adding Drupal VM to a project, you should run:

`composer require --dev geerlingguy/drupal-vm:^4.0`
This will add geerlingguy/drupal-vm to a require-dev section in your composer.json file, and then you can easily choose to not include that project in the deployed codebase.

Commiting your .lock file
The Composer documentation on the lock file bolds the line:

**Commit your application's composer.lock (along with composer.json) into version control.**

For good reason---one of the best features of any package manager is the ability to 'lock in' a set of dependencies at a particular version or commit hash, so every copy of the codebase can be completely identical (assuming people haven't gone around git --force pushing changes to the libraries you use!), even if you don't include any of the code in your project.

Ideally, a project would just include a composer.json file, a composer.lock file, and any custom code (and config files). Everything else would be downloaded and 'filled in' by Composer. The lock file makes this possible.

Patching modules
----
Acquia's BLT the composer-patches project, which is what it says on the tin: "Simple patches plugin for Composer."

Use is fairly simple: first, `composer require cweagans/composer-patches:^1.0`, then add a patches section to the extra section of your composer.json file:

    "extra": {
        "patches": {
            "acquia/lightning": {
                "New LightningExtension subcontexts do not autoload": "https://www.drupal.org/files/issues/2836258-3-lightning-extension-autoload.patch"
            },
            "drupal/core": {
                "Exposed date view filter fix": "https://www.drupal.org/files/issues/2369119-145_0.patch"
            }
    }

Once you've added a patch, you might wonder how to get Composer to apply the patch and update composer.lock while still maintaining the same version you currently have (instead of running composer update drupal/module which may or may not update/change versions of the module).

The safest way is to run composer update none (a handy trick yet again!), which allows Composer to delete the module in question (or core), then download the same version anew, and apply the specified patch.

