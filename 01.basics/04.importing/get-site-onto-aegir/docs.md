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
Get Your Site Into Aegir

To import your site into Aegir, you must first\
[get your database and files into your Aegir
account](get-database-files).\
Then, you can follow the steps in this doc to set up your new site.

Task: Import Your Site Into Aegir
---------------------------------

Importing your old site onto an Aegir [platform](platform) is
straightforward. Follow\
each step carefully, and you should have no problems.

1.  Get your database and files into your Aegir account, following\
    [the steps in this doc](get-database-files).

<!-- -->

1.  If your site will be on a new custom platform, you'll also need to\
    add your custom platform before you can\
    proceed. Follow the steps in [this doc](add-custom-platform)

<!-- -->

1.  [Create a new site](new-site-built-in) on your target platform.\
    Use your **actual domain name**. If the site is `foo.com`, use\
    `foo.com`, not some temporary domain or subdomain.

**** If you have been developing the site locally, see "Why Use the
Final Domain, Then Rename Twice?" below.

1.  Copy all the old site's `files` into `sites/foo.com/files/` on the
    new site.

**** Example:
`cp -af ~/static/old-site/sites/default/files/* /path/to/platform/sites/foo.com/files/`

**** If you have also stored files in `sites/foo.com/files`, copy those
files as well.

1.  If your site used additional modules at `sites/all/modules/` and/or\
    `sites/foo.com/modules`, you need to copy them:

\#\# Copy any "contrib" modules (modules you downloaded from
drupal.org)\
from their directory within `~/static/old-site/sites/` into\
`sites/all/modules` on the target platform.

****\* Look for modules in all possible locations on the old site:\
`sites/all/modules`, `sites/default/modules`, and\
`sites/foo.com/modules`. No matter where you stored them, contrib\
modules should almost always go into `sites/all/modules` on the target\
platform. (See "Always Put Contrib Modules In `sites/all/modules`"\
below.)

****\* If, instead of copying old modules, you download any modules\
directly from `drupal.org` into the target platform, make sure to fix\
permissions with `chmod -R 775`.

\#\# Copy any "custom" modules for this site into
`sites/foo.com/modules`.

\#\# Repeat these steps for themes and libraries.

****\* Contrib themes go into `sites/all/themes`, custom themes into
`sites/foo.com/themes`.

****\* Libraries go into `sites/all/libraries`, unless module
documentation specifies otherwise.

1.  Import your uploaded database into the new site with `drush sqlc`.
    Example commands:

\#\# `cd /path/to/platform/sites/foo.com/`

\#\# `drush sqlc < /data/disk/USER/static/dump.sql`

****\* Note the full path to the dump file. Don't use a relative path,
like `~/static`.

****\* Replace USER with your [BOA](boa) username. This is your FTP/SSH
username\
minus the ending `.ftp`. If your FTP/SSH username is `12345678.ftp`,\
your BOA username is `12345678`. Your SSH username always appears in\
your SSH prompt.

\#\# Rebuild the new site's registry.

****\* Use the "Rebuild Registry" task in Aegir.

****\* Or `cd` to `sites/foo.com/` and run `drush rr`.

1.  In Aegir, rename the site with the "Migrate" task **twice**.

\#\# First rename the site to a temporary subdomain (example:
`temp.foo.com`).

\#\# Then rename the site back to your final domain (`foo.com`).

****\* (See "Why Use the Final Domain, Then Rename Twice?" below.)

1.  Finally, run the "Verify" task on the site.

With this final "Verify", all paths to images should be properly\
rewritten, both in the `files` table and in the `node_revision` table.

Done! Enjoy your new site.

More Information
----------------

To avoid potential problems, you may want to read the following\
information before you import your first site.

### Does Your Drupal 6 or Drupal 5 Site Have to Be Based on Pressflow?

We do not use vanilla Drupal for our Drupal 6 or Drupal 5 platforms.\
Instead, we use [Pressflow](pressflow).

However, we expect that your Drupal 6 or Drupal 5 site is probably\
based on vanilla Drupal. No problem. We suggest that you:

1.  [Make a custom platform](add-custom-platform) based on your
    old environment.

<!-- -->

1.  Import your site to this custom platform.

<!-- -->

1.  Migrate your site onto a Pressflow platform:

**** You can use one of our built-in Pressflow platforms.

**** Or you can create your own platform based on Pressflow core.

Note that **Pressflow is required** for all *live* Drupal 6 and Drupal
5\
sites. You may not build a custom platform based on vanilla Drupal 6\
or Drupal 5, except as a temporary platform to use while migrating\
your old sites to Pressflow.

Please migrate your site to Pressflow **before pointing a live domain**\
name to your Aegir instance IP address. Running vanilla Drupal 6 or\
Drupal 5 sites is not allowed, and breaks\
our [Acceptable Use Policy](acceptable-use-policy).

Also, with the release of Drupal 7, **Drupal 5 is no longer officially
supported**,\
so you should upgrade to a Pressflow-based Drupal 6 platform
immediately.

### If Your `files` Directory Is Over 500MB

When your site's `files/` directory is big (500MB or more), it should\
be moved to a directory in `~/static`, and then symlinked back to\
`sites/foo.com/files`.

Several Aegir tasks create a full, compressed archive of the entire\
`sites/foo.com/` directory. If the `files/` directory is too big,\
these tasks will fail, because the servers run out of RAM and CPU. By\
using a symlink, these archives will only store the link, instead of\
all the actual files.

Root access is required to make this link. On Omega8.cc, you can't do\
this yourself, but please [contact us](support), and we'll be happy to\
make this symlink for you.

If you have root access, the steps might look like this:

    mv /path/to/platform/sites/foo.com/files /data/disk/USER/static/foo.com_files
    ln -s  /data/disk/USER/static/foo.com_files /path/to/platform/sites/foo.com/files

Replace USER with your BOA username.

### Always Put Contrib Modules in `sites/all/modules/`

In normal Drupal, it may not seem to matter much whether you store\
modules in `sites/all/modules`, `sites/default/modules`, or the\
site-specific directory, such as `sites/foo.com/modules`.

But on Aegir, it's critical that you store all "contrib" modules\
(modules you download from drupal.org) in `sites/all/modules`. This is\
the platform-wide directory. This single copy of the module will be\
used for all the sites.

Aegir tracks the platform-wide modules. When you migrate your site to\
a new platform, Aegir will help, comparing the module versions on both\
platforms, applying needed database updates, and saving a backup in\
case anything breaks.

If you instead store a contrib module in `sites/foo.com/modules`, you
lose all\
these benefits. In a migration, Aegir ignores everything in\
`sites/foo.com/`, and simply copies the files to the new platform.

Plus, you can easily forget that you stashed a copy here. Even if you\
migrate the site to a platform with a newer version, the old, insecure\
copy of the module will [override](override-module) the new version.

You should only use `sites/foo.com/modules` for custom, one-off\
modules that you write yourself, and are unique to this site.

These rules also apply to themes. Of course, many sites have a unique,\
custom theme or subtheme, and it makes sense to store this in\
`sites/foo.com/themes`.

### Why Use the Final Domain, Then Rename Twice?

When you create the blank site, why must you use your final, live\
domain name (like `foo.com`), then rename the site twice? This process\
ensures that all the paths saved in your database are properly\
rewritten.

For instance, an image stored at `sites/default/files/image.png` must\
get its path rewritten to `sites/foo.com/files/image.png`.

This renaming process should fix all paths, both in the `files` table
and also\
in your content.

However, there are places where hardcoded paths can't be replaced\
automatically. One example is your custom theme settings. If any paths\
are still broken, you'll need to fix them manually.

#### If You Have Been Developing the Site Locally

Note: If you have been **developing this site locally**, with a name
like\
`domain.local`, but you now want it to be a live site, like `foo.com`,\
the steps are slightly different:

1.  Create the initial site with the **local name** (like
    `domain.local`),\
    instead of the final domain name.

<!-- -->

1.  Then, when the time comes to rename the site twice, follow the
    steps\
    as usual. Rename to a temporary domain name, then to the final\
    domain name (`foo.com`).

\[add-custom-platform\]\
\[built-in-platform-list\]\
\[new-site-built-in-platform\]\
\[pressflow\]http://pressflow.org\
\[acceptable-use-policy\]http://omega8.cc/aup

\[platform\]\
\[get-database-files\]\
\[add-custom-platform\]\
\[boa\]\
\[override-module\]
