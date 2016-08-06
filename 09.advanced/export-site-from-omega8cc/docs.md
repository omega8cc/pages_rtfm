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
How to Export Your Site From Aegir

You can export any of your Drupal sites from our Hosted Aegir\
environment onto any other host, to another Aegir system or\
as a standalone Drupal site, using the steps outlined below.

Overview
--------

To export your site, you will need three separate [pieces]()

-   A database dump, saved in the database.sql file

<!-- -->

-   Everything from the `sites/foo.com/` directory

<!-- -->

-   The complete [platform](platform) underneath this site

Step-by-Step
------------

\*Step 1: Log into the Aegir control panel and run the "Backup" task on
your\
site.\*

This will create a single, compressed archive in your account\
`~/backups/` directory. This archive includes the database dump and\
a complete `sites/foo.com/` directory.

**Step 2: Copy this archive file to your local drive.**

You can use SFTP or FTPS. Or, with rsync over SSH, you can copy\
directly to another server.

**Step 3: Copy the platform directories and files.**

If you've been using your own [custom platform](custom-platform), you\
have full access to all the files, so you can copy them easily.

With our [built-in platforms](built-in-platforms), the best method is\
to use the `rsync` command. Here is the full command:


&lt;code&gt;rsync -avzuL -e ssh &lt;strong&gt;user.ftp@host.ip:/path/to/platform /local/path/&lt;/strong&gt;&lt;/code&gt;

This command relies on the `-L` option, so make sure you get those\
options correct.

You must replace the bold **placeholders** with your details:

-   Replace `user.ftp` with your SSH/FTPS account username.
-   Replace `host.ip` with the domain where you log into Aegir
    control panel.
-   Use full system paths (see below).

With both the Aegir backup archive from `~/backups/` and the complete\
platform files, you can import your Drupal site into any other Aegir\
instance. You can also rebuild it as a standalone Drupal site.

Caution
-------

### Help! "rsync" Copies All the Other Sites

If you copy a platform with that `rsync` command, you will copy the\
files of other sites. To avoid this,\
check out the `--exclude` option for `rsync`. (Run `rsync --help` for
details.)

### Don't Use Symlinks in the Path to the Platform

When copying the platform with the `rsync` command above, you'll need\
to use the full system paths. Don't use relative symlinks that begin\
with `~/platforms` or `~/clients` or `~/static`.

You can find the full path to the platform in any of these ways:

-   Log into Aegir and check the platform node. This page will include\
    the full path to the platform.

<!-- -->

-   SSH in, switch to the site directory, and type `drush status`.\
    It will show many details, including the "Drupal root", which is\
    the full path you are looking for.

\[platform\]link

\[custom-platform\]http://omega8.cc/how-to-add-custom-platform-properly-140

\[built-in-platforms\]link
