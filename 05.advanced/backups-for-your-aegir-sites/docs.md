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
Backups for Your Aegir Sites at Omega8.cc

Backups are essential for preserving your sites (and your sanity). At
Omega8.cc, we offer extra protection through free, automated backups.
Aegir itself also performs many backups automatically. You can access
these backups easily.

Task: How to Access Your Backups
--------------------------------

With so many automated backups, you usually don't have to *make*
backups. Instead, here is how to *use* the backups you already have.

### Step-by-Step: Access Your Backups

There are several ways to access your backups.

-   Edit your site within Aegir, and use the `Restore` task. If there
    are multiple backups available, you can select one.

-   You can access these Aegir backup archives directly, via
    `FTPS/SFTP`
    and `SSH`, at `~/backups/` in your home directory.

-   If you can't find what you need through an Aegir backup, you have
    further [Idera](r1soft) backups available (see below). You can
    request an
    Idera backup through our [support form](support). (There is no
    direct access to these backups.)

Task: How to Maintain Your Own Backups
--------------------------------------

If you prefer to maintain your own backups, use the [**Backup and
Migrate**](backup-migrate)
module and its "scheduled backups" option.

### Step-by-Step: Maintain Backups with "Backup and Migrate"

-   Download the Backup and Migrate module (`backup_migrate`).

-   Enable the Backup and Migrate module for your site.

-   Configure your backups. (Drupal 7:
    `admin/config/system/backup_migrate/`). You can run a *manual*
    backup and/or set up *scheduled* backups. Both kinds will save to
    your site's `private/` directory. Example:
    `sites/foo.com/private/files/backup_migrate/manual/`

-   Copy these backup archives to your own server or local computer.
    Tools for copying include `SFTP/FTPS` and `rsync` over `SSH`.

-   You **must copy all backups before Monday**. Every Monday, we
    **purge**
    all backup archives to keep your Omega8.cc disk space clean.
    Archives are purged from each site's `private/backup_migrate`
    directory, from `~/backups/`, and from anywhere else in your home
    directory. (See below.)

Fortunately, a week is plenty of time to copy off the files you need.
With enough disk space, you can store all the backups you like.

More Information
----------------

### Is There Any Charge for Requesting an Idera Backup?

We are happy to provide an Idera backup to you for **free**, as long as:

-   You only make this request occasionally,

-   and it takes less than 15 minutes of work.

In other cases, this service will cost $152 USD per hour.

### Are "Backup and Migrate" Backups Protected?

Yes. On the BOA system, everything under `private/` is inaccessible to
the public. You must log in with `SSH` or `SFTP/FTPS` to access these
files.

### How Does Omega8.cc Make Automatic Backups?

At Omega8.cc, we maintain daily, duplicate, block level (not just file
level) professional backups for all your files and databases, using
[Idera](r1soft) software.

We store two copies of these backups:

-   A **local** copy, in the the same facility where your system is
    hosted.

-   A **remote** copy, in a remote facility. The remote backup gives
    you
    extra security.

All backups are versioned and rotated. The backups are rotated daily,
so there is always a copy of all your files from the last 7 days.

A third, additional copy of your daily **database** backups (not the
files) is also stored on the same local server. These database backups
are rotated weekly, and also archived both locally and remotely.

The result? You always have daily backups of:

-   the last 7 days for your **files**
-   the last 14 days for your **databases**

### How Do Aegir Tasks Make Automatic Backups?

Several Aegir tasks generate backups automatically.

-   The `Backup` task, obviously, creates a backup, which you can later
    restore with the `Restore` task.

-   When you later `Restore`, Aegir also backs up your *current* site
    before restoring the backup!

-   `Clone` and `Migrate` also create backups. Even when you only use
    `Migrate` to "Rename" your site by migrating the site to the same
    platform, this task creates a backup.

These backups are compressed archives. Each backup includes:

-   all site files from the `sites/foo.com/` directory

-   a database dump of the site

(Note that the backup does *not* include the core code or the modules
in that site's [platform](platform.))

### If Your Old Aegir Backups Are Missing

Aegir makes many automatic backups, and these archives could fill your
disk space very quickly.

At Omega8.cc, we **purge** the built-in Aegir `~/backups/` directory
**weekly**, on Monday morning. We also purge each site's private
`backup_migrate` directory.

If you try to `Restore` an old backup, and it's no longer available,
don't panic. Remember, you can always request a backup via our
[support form](support) as long as it is within the last 7 days limit
(or the last 14 days limit for database-only archives).

Caution
-------

Note that you can’t use your Aegir instance disk space as
an archive space. Any files, archives or backups found in your FTPS/SSH
account home directory, or in `~/static`, or in any other directory
which is not a part of a valid Drupal multisite (Aegir platform)
structure
will be **deleted automatically** once discovered, without any notice,
and we will not accept any related backup recovery requests.

[supported-module-list]http://omega8.cc/supported-enabled-disabled-a-complete-list-150

[backup-migrate]http://drupal.org/project/backup_migrate

[support]http://omega8.cc/support

[r1soft]http://r1soft.idera.com/server-backup-enterprise

[platform]link

[customize-built-in]link
