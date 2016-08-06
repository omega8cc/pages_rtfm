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
Add a Module or Theme to a Built-in Platform

When you create a new Drupal site on Aegir, you get a choice of many
[built-in platforms](built-in-platforms). Each platform offers a
particular collection of useful modules. But you can add modules and
themes to these built-in platforms.

Once you add a module or theme to your platform, you can enable it for
any site on the platform.

Task: Add a Module or Theme to a Platform
-----------------------------------------

1.  Upload your module or theme to `sites/all/modules/` or
    `sites/all/themes/` on the platform.

1.  Within `sites/all/modules/` or `sites/all/themes/`, run
    `chmod -R 775` to set correct permissions.

1.  In Aegir, run `Verify` on this platform.

1.  For each site on the platform, rebuild the registry with `drush rr`
    or the `Rebuild registry` Aegir task.

1.  Enable the module on the site(s) where you want to use it. For each
    site, you may wish to test the new module on a clone first.

References
----------

[Add a Module or Theme to a Site on Aegir](add-module-site)

[Override a Module or Theme on Aegir](override-module)

[Customize Our Built-in Platforms Instead of Adding Custom
Platforms.](link)

[hybrid-storage]http://omega8.cc/hybrid-storage-high-speed-big-space-237

[extra-modules-available]http://omega8.cc/extra-modules-available-in-all-platforms-123

[custom-platform]http://omega8.cc/how-to-add-custom-platform-properly-140

[aegir-basics]http://omega8.cc/library/aegir-basics

[built-in-platforms]link

[never-hack-core]http://drupal.org/best-practices/do-not-hack-core

[sites-all-modules]link

[migrate-platform]link

[add-custom-platform]link
