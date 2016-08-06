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
How to Edit the "settings.php" File on Aegir

On Aegir, you can't edit `settings.php` directly. Instead, you must\
add your customizations to `local.settings.php`, a file in the same\
directory as `settings.php`.

Problem
-------

Editing `local.settings.php` is dangerous -- you're basically doing\
open-heart surgery on your web site. To avoid accidental mistakes,\
Aegir makes you go through a few extra steps every time you want to\
edit `local.settings.php`, which is not writable by default.

Solution
--------

Here's how to temporarily make `local.settings.php` writable.

1.  Create an empty control file at:
    `sites/foo.com/modules/local-allow.info`\
    (`foo.com` is an example -- replace it with your site's real
    domain name).

1.  Go to the Aegir control panel and run the "Reset password" task on\
    your site. Wait until the task finishes. Now `local.settings.php`
    is\
    writable.

1.  Edit `local.settings.php` and add your customizations, either on
    the\
    command line or via an SFTP or FTPS client and desktop editor.

1.  When you're finished, **check your web site**. This is critical.
    Really.\
    Even a minor typo in `local.settings.php` can bring down your\
    entire web site with a fatal WSOD (White Screen of Death). Log in
    as\
    the admin user and make sure the pages are loading properly.

1.  When you are certain that your site is not broken, run the "Verify"\
    task on your site in the Aegir control panel. This will return\
    `local.settings.php` to its safe, unwritable state.

1.  Finally, remove the `local-allow.info` control file. Otherwise, you
    will\
    accidentally unprotect `local.settings.php` next time you run
    "Reset\
    password."

Caution
-------

### Help! My Site is Broken And I Can't Fix It!

When editing `local.settings.php`, it is possible to break your site\
and be unable to fix it without our help. If you:

-   Edit `local.settings.php` and enter a typo which causes a WSOD,

-   then run "Verify" with a broken `local.settings.php`,

-   you will find that your site is broken, and `local.settings.php` is\
    unwritable again.

-   If you try to fix things by running "Reset password" to unlock\
    `local.settings.php`,

-   the task will fail, because your site is broken!

Yes, Aegir will manage to "Verify" your broken site, lock your broken\
`local.settings.php`, and then be unable to *unlock* the very file\
that's causing the breakage!

The best way to avoid this disaster is to check your site very\
carefully before you run "Verify" and thus "save your changes" to\
`local.settings.php`.

However, if you do break your site like this, hope is not lost. Open a\
[support ticket](http://omega8.cc/support), and we'll fix things.
