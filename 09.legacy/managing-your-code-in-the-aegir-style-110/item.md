---
title: Managing your code in the Aegir Style
slug: managing-your-code-in-the-aegir-style-110
menu: Managing your code in the Aegir Style
date: 09-01-2013
published: true
publish_date: 09-01-2013
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

Aegir “enforces” some good practices, but not to make your work fancy in the “Aegir Style”, rather to make it secure, effective and re-usable (modular). For example, it manages some secure permissions to save you headaches later, when you will try to really use the full Aegir power to migrate, clone, batch upgrade many sites etc. It also fails and reverts any changes if any task causes errors, so you can debug your sites issues and try again until it works without any issues.

Of course Aegir doesn’t help you in maintaining modules installation and upgrades, but it allows you to migrate Sites between Platforms, so you have to create a new Platform with new modules versions and then migrate the Site, when you wish to upgrade it securely, with automatic and instant roll-back, if anything goes wrong in the process. It is always recommended to clone the Site in the existing Platform and test migration of the cloned Site first, before trying it with your live Site. You may want to read a few very useful, related articles:

 “Your Drupal Site Upgrade — Safe Workflow »”:https://omega8.cc/your-drupal-site-upgrade-safe-workflow-298   
 “Import your sites to Aegir in 8 easy steps »”:https://omega8.cc/import-your-sites-to-aegir-in-8-easy-steps-109   
 “How to add custom platform properly? »”:https://omega8.cc/how-to-add-custom-platform-properly-140   
 “The best recipes for disaster – a must read »”:https://omega8.cc/the-best-recipes-for-disaster-139   
 “Are there any specific good habits to learn? »”:https://omega8.cc/are-there-any-specific-good-habits-to-learn-116   
 “Migrate sites between installation profiles »”:https://omega8.cc/migrate-sites-between-installation-profiles-111

To better understand the logic behind Aegir and associated tools, it helps when you start thinking that the Site is not an App, it is the Installation Profile which is an App, and the Site is only this App’s provisioned instance, while the Makefile is the easiest way to define and create a Platform, and the Platform is an environment where your Apps (the installation profiles) live.

 The recommended (and also more advanced) way to manage your Sites code is to use Makefiles (and then “Drush Make”:http://drupal.org/project/drush\_make) to build your Platforms, apply patches to contrib or custom modules etc, then using “Profiler module”:http://drupal.org/project/profiler to create your custom Installation Profile and manage in your Git repo just your Makefiles, your Installation Profiles and only your custom modules and patches – \*in a separate repo per module and per theme\*.

Note that you could have more than one Installation Profile per Platform, so there is no need to multiply Platforms, when they share most of the code, just differently configured/used.

Working that way you will be able to easily re-use your work, to create new Installation Profiles, Platforms, and avoid duplication.

A must-read articles by “Bill Powell”:http://billpowellisalive.com on cms.about.com

 [What Is a Drupal Distribution? »](http://bit.ly/ZsXOCA)   
 [What Is a Drupal Installation Profile? »](http://bit.ly/UPgJDX)   
 [Aegir Platforms: A New Model for Thinking About Drupal Web Sites »](http://bit.ly/Uta9Ak)   
 [What Is a “Platform” on Aegir? »](http://bit.ly/RA0B9z)   
 [How to Organize Your Modules Into an Aegir Drupal Platform »](http://bit.ly/TEFoLA)   
 [Choose Drupal Modules Wisely »](http://bit.ly/RzXSgh)   
 [How Aegir “Upgrades” Your Drupal Site By Migrating Between Platforms »](http://bit.ly/138JKyg)   
 [Never Upgrade Drupal Modules. Instead, Make New Aegir Platforms. »](http://bit.ly/UPk1aa)   
 [Website Changes Should Be Tested on a Copy »](http://bit.ly/XbHmSY)

Recommended, related presentation by “Matt Petrowsky”:http://gotdrupal.com/:

Other recommended, related articles:

 “Core Conceptions »”:https://omega8.cc/compare/conceptions   
 “Automating Drupal Development: Makefiles, Features and beyond »”:http://nuvole.org/blog/2012/jun/25/automating-drupal-development-makefiles-features-and-beyond   
 “Building and Maintaining a Distribution in Drupal 7 with Features »”:http://nuvole.org/blog/2011/aug/24/bulding-and-maintaining-drupal-distributions   
 “Drush Make – Drupal Distributions Packaging Automation Tool »”:http://drupal.org/node/625094   
 “Drush Make theory for happy profile development »”:http://drupal.org/node/1006620   
 “Aegir hosting system »”:http://drupal.org/node/1080220