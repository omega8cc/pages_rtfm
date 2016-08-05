You can also *override*\
existing modules and themes with a new version.

Overview: *Override* a Module or Theme
--------------------------------------

You can *override* or module or theme that's already in the platform.\
For instance, you can upload a newer or development version. Drupal\
will use the version you have uploaded.

You can override for the entire platform (`sites/all/modules`) or for\
one site (`sites/foo.com/modules`).

Drupal decides which version of a module or theme to run based on its\
location in the filesystem. The order of precedence is:

1.  `sites/foo.com/modules/`
2.  `sites/all/modules`
3.  the platform `modules/` directory
4.  the platform `profiles/foo/modules` directory

**Caution:** Overriding the wrong module or theme can \*break all the\
sites on your platform\*. In general, instead of upgrading, you should\
prepare a new platorm, and [migrate each site to the new
platform](migrate-platform).\
Please read the "Caution" section below before deciding to override.

Step-by-Step: *Override a Module or Theme for a Platform*
---------------------------------------------------------

**Caution**: You should almost never override a module for an entire
platform.\
But if you insist, here's how.

1.  Upload your module or theme to `sites/all/modules/` or
    `sites/all/themes/` on the platform.

<!-- -->

1.  Within `sites/all/modules/` or `sites/all/themes/`, run
    `chmod -R 775` to set correct permissions.

<!-- -->

1.  For each site on the platform, rebuild the registry with `drush rr`
    or the `Rebuild registry` Aegir task.

<!-- -->

1.  For each site on the platform, run the `Backup` Aegir task.

<!-- -->

1.  For each site on the platform, apply any necessary database updates.
    Use `drush dbup` or browse to `http:/foo.com/update.php`

Step-by-Step: *Override* a Module or Theme for One Site
-------------------------------------------------------

Overriding a module for one site is still dangerous, but at least you
can quickly test it first on a copy.

1.  Make a test copy of your live site with the `Clone` task in Aegir.
    Example: `bar.dev.foo.com`

<!-- -->

1.  Upload your module or theme to the site-specific directory **of the
    test site**. Example: `sites/bar.dev.foo.com/modules/`

<!-- -->

1.  Within this directory, run `chmod -R 775` to set
    correct permissions.

<!-- -->

1.  Rebuild the registry with `drush rr` or the `Rebuild registry` Aegir
    task for the site.

<!-- -->

1.  In Aegir, run the `Backup` task for the test site.

<!-- -->

1.  Apply any module updates. Use `drush dbup` or browse to\
    `http://bar.dev.foo.com/update.php`.

<!-- -->

1.  Inspect the test site. If nothing has broken, delete the test site,\
    and repeat these steps for your live site.

Caution
-------

### Don't Override an "Older" Module Without Research

Sometimes the built-in platforms seem to have "outdated" modules.\
Don't assume a lazy maintainer! The newer version might have an\
incompatibility or a bug that would bring down all the sites on the\
platform. Research carefully before deciding to override.

### Never Hack Core!

Although you can override modules, you can't override core. If you\
want to patch core, you'll need to\
[build your own custom platform.](custom-platform)\
(Please don't request that we patch core on a built-in platform.)

But you've heard the saying, right? [*Never hack
core!*](never-hack-core)\
We strongly encourage you to avoid patching core, even on your own
custom platform.

In fact, the core we offer on our built-in platforms has *already* had\
important patches and improvements applied. We optimize core for our\
hosting.

If you choose to build your own platforms, we suggest you use the same\
core that we offer with our built-in platforms.\
We publish our customized cores at our [Omega8cc GitHub\
account](https://github.com/omega8cc/):

-   [Drupal 7](https://github.com/omega8cc/7x/) from Omega8cc
-   [Pressflow (Drupal 6)](https://github.com/omega8cc/pressflow6/) from
    Omega8cc

