---
title: Extra modules available in all platforms
slug: extra-modules-available-in-all-platforms-123
menu: Extra modules available in all platforms
date: 30-06-2011
published: true
publish_date: 30-06-2011
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="extra-q"></a>

QIs there a list of contrib modules added by default in all 6.x and 7.x platforms, even in my custom platforms created in the /static directory?

<a name="extra-a"></a>

AThe list of extra contrib modules available in all 6.x and 7.x platforms can be modified with every new “BOA”:http://omega8.cc/open-source/projects release/upgrade, and for latest stable release you can find it [here](/supported-enabled-disabled-a-complete-list-150). All those extra modules coming by default with our 6.x and 7.x platforms will be automagically added (symlinked) also in all your custom platforms – but only when there is at least one site already created in the custom platform. This automated magic takes place every morning, so it is probably a good idea to create a dummy site in your custom platform one day before you plan to start working on it, to have all those extra modules included.

<a name="extra-q"></a>

QWhy all those extra contrib modules are symlinked in the platform core modules directory and not in the @sites/all/modules@ or in the profiles?

<a name="extra-a"></a>

AFor 6.x platforms the extra contrib modules are symlinked in the platform root @/modules /o\_contrib@ directory and for 7.x platforms in the platform root @/modules /o\_contrib\_seven@ directory. We did it for two reasons – to not modify original, built-in contrib space normally located in the platform root @/profiles /name /modules@ space and to give you possibility to override them with your own copies / versions either in the platform-wide space @/sites /all /modules@ or site-specific space @/sites /foo.com /modules@. It is possible thanks to Drupal native logic, where platform-wide space takes precedence over profiles and core modules space, while site-specific space takes precedence over platform-wide space. One warning however – we recommend to never use @/sites /foo.com /modules@, as this space is never checked by Aegir for compatibility on upgrade / migrate between platforms and may even cause “some serious problems”:http://omega8.cc/the-best-recipes-for-disaster-139 during clone / migrate tasks.

<a name="extra-a"></a>

!Note that Aegir knows nothing about these extra modules if you didn’t re-verify the custom platform \_after\_ our system created the symlink. You have to re-verify the custom platform once the symlink is in place, to give Aegir a chance to register these extra modules, so they will show up on the platforms comparison list.