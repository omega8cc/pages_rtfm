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
How to Use robots.txt on Aegir

Aegir, being based on the Drupal Multisite feature, requires that every
site
has its own copy of the "robots.txt" file. You can't use a single,
central "robots.txt" file in the platform root directory, because it
would be
shared across all sites on the same platform.

Problem: You need to customize "robots.txt" per site
----------------------------------------------------

The BOA system enables "robots.txt" support for every hosted site, but
it comes
with the contents of the default Drupal "robots.txt" file. If your
Drupal site
on Aegir needs a custom "robots.txt" file, you can't put
"robots.txt" in the root of your platform directory, because the BOA
system
will delete it, to meet requirements of supported RobotsTxt module.

Solution 1: RobotsTxt Module
----------------------------

Use the [RobotsTxt](http://drupal.org/project/robotstxt) module. With
RobotsTxt, you can configure `robots.txt` for each site separately.

Drupal 6: `admin/settings/robotstxt`

Drupal 7: `admin/config/search/robotstxt`

You don't need to download RobotsTxt. This module is on the
[list of modules that come bundled](supported-enabled-disabled) on all
BOA
[built-in platforms,](built-in-platforms). RobotsTxt is enabled by
default.

Solution 2: Put "robots.txt" in "files/"
----------------------------------------

The downside to RobotsTxt is that, even with caching, the bots are
still hitting Drupal.

For better performance, upload a separate, unique `robots.txt` file to
the `files/` directory for any site.

For instance, for `foo.com`, you want `/sites/foo.com/files/robots.txt`.

Thanks to our built-in Nginx rewrites, a `robots.txt` at this location
will take precedence over the RobotsTxt module for that site.

Automatically generated "robots.txt"
------------------------------------

Starting with BOA-2.0.10, the system will generate this static file
automatically for every active site. This means that if you make
any changes in the RobotsTxt module configuration, they will not be
active until you delete the existing `/sites/foo.com/files/robots.txt`
static file. This will allow the system to regenerate it from updated
settings.

Domain Access compatibility
---------------------------

Starting with BOA-2.0.10, our built-in Nginx rewrites support
additional,
per-domain "robots.txt" files located in the same
`/sites/foo.com/files/`
directory. These extra files can't be generated automatically, and they
are also completely independent from RobotsTxt module. These files must
be created and managed mnaually.

They should follow this naming convention:

`/sites/foo.com/files/foo.com.robots.txt`
`/sites/foo.com/files/bar.com.robots.txt`

Nginx will try to find the file that matches the currently requested
domain.
For example, it will automatically map a `http://foo.com/robots.txt`
request
to the file `/sites/foo.com/files/foo.com.robots.txt` (if this file
exists).

[add-custom-platform]:link

[support-enabled-disabled]:http://omega8.cc/supported-enabled-disabled-a-complete-list-150

[built-in-platforms]:link
