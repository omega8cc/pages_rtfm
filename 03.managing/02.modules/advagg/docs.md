---
title: TITLE
slug: URI
menu: MENU
date: 08-08-2016
published: true
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /URI
---

How to Use the AdvAgg Module on Aegir

Does the layout on your Drupal site break whenever you clear the
cache? If so, you may need the AdvAgg module.

h2. Problem: Clearing Caches Breaks the Layout

When you're developing a web site, especially the theme, you have to
clear the caches to see the changes you make to CSS and Javascript.
However, when you clear the caches, the CSS and Javascript seem to vanish.
Your site layout breaks, like it's 1999.

h2. Solution: Enable the built-in AdvAgg Module

The problem is that CSS and Javascript files are being _aggregated_
(see below for an explanation). You can solve this problem with the
"AdvAgg":http://drupal.org/project/advagg module. This module requires
special configuration, but don't worry, everything is already pre-configured
for you, and the module is already "included":extra-builtin-modules
in every Drupal 6 and Drupal 7 platform. It is enough to simply enable
all its sub-modules. There are a few of them; it is not a single module.

h3. Caution

h4. Enabling AdvAgg Slows Down My Site!

If you enable AdvAgg, requests and page views will suddenly take more
time to process. Don't worry. This is a normal, one-time event, as
AdvAgg generates the initial aggregated files.

We recommend that you also enable
the "HTTPRL":http://drupal.org/project/httprl module, which is also "included":extra-builtin-modules. It will improve
the performance of AdvAgg.

h4. My CSS/Javascript Files Won't Update!

If you enable AdvAgg, your site will begin to aggregate CSS and
Javascript files using the advanced aggregation. When you edit
the CSS or Javascript source files, you will need to rebuild some of
the aggregated bundles to see your changes.

However, you no longer need to use the old @Clear cached data@ button
on the Performance page for this purpose. (In fact, it won't do anything.)

Instead, use the smart @Flush AdvAgg Cache@ button at
@admin/settings/advagg@. This will intelligently rebuild only the aggregated
bundles which include the modified file, and you'll be able to see your changes.
Since the filenames of the aggregated bundles do not change, the layout
will not break when you rebuild them.

h2. More Information

h3. Without AdvAgg, Why Does Clearing the Caches Break the Layout?

Without AdvAgg, CSS and Javascript files are normally _aggregated_
by Drupal default. We enable simple aggregation for you automatically.
Files are combined into single (bundled) CSS and Javascript files with unique names.

When you use the @clear cached data@ button on the admin Performance
page, here's what happens:

* the aggregated CSS and Javascript files are purged
* new aggregated files are generated with new names
* but the cached versions of the site pages still reference the _old_ aggregated files

Now your site is full of old paths. As far as Drupal can tell, the CSS
and Javascript files are all missing. AdvAgg to the rescue!

[extra-builtin-modules]
