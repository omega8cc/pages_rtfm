You can add any module or theme, either for the entire platform or for\
a particular site. In general, if you download the module from\
drupal.org, you should add it to the entire platform. If you have made\
the module or theme yourself, and it is only for one site, it is safe\
to add it to the site.

*Adding* a module does not automatically *enable* it. You can add a\
module to a platform even if only one site will have it enabled.

Step-by-Step: Add a Module or Theme to One Site
-----------------------------------------------

Caution: you should only use this method for a module or theme that\
you maintain yourself and is unique to this site.

1.  Upload your module or theme to the site-specific directory. If your\
    site is `foo.com`, this will be `sites/foo.com/modules/` or\
    `sites/foo.com/themes/`.

<!-- -->

1.  Within this directory, run `chmod -R 775` to set
    correct permissions.

<!-- -->

1.  Rebuild the registry with `drush rr` or the `Rebuild registry` Aegir
    task for the site.

<!-- -->

1.  Enable the module.

### Avoid Breaking Your Site(s)

Adding a new module can break your site. You should always **clone your
live site** and\
**test the new module or theme on the clone**.

In general, a new module can't cause damage unless you enable it. In\
very rare cases, the mere presence of a module directory can cause\
problems for other modules, but this is unusual.

Overrides are even more dangerous, since they *automatically* upgrade\
(or downgrade!) the site, with no built-in way to roll back your\
changes. If you make this upgrade for the platform, you could break\
all the sites in one fell stroke.

Instead, make a new platform, with the new versions of the modules.\
Then [migrate each site to the new platform](migrate-platform). If you\
follow all the steps, Aegir protects your sites from permanent damage.\
You can safely restore your sites if they break.

### Always Put Contrib Modules in `sites/all/modules`

When you upload a module from drupal.org, it should go into\
`sites/all/modules`. Same for themes. If you download it, put it in\
`sites/all/themes`. You want one copy for the whole platform.

If you instead put a contrib module in the site-specific\
`sites/foo.com/modules/`, you will eventually forget about it, and\
this **old module will make your site insecure**. Even if you upgrade\
the platform version of this module in `sites/all/modules`, your old,\
insecure, site-specific version will silently override it.

The only exception is if you *want* to override a module on a\
particular site. But the safe option is to prepare an upgraded\
platform and migrate the site.
