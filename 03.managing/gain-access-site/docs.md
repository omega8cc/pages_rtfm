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
Log In Without a Password

You can log into any site on your Aegir instance without the password.
As long as you can access your Aegir admin panel or [ssh](ssh) into
your account, you can log in to a Drupal site.

Task: Use a Login Link Instead of a Password
--------------------------------------------

### Using the Aegir Admin Panel:

1.  Run the "Reset password" task.

1.  Click the "Log in" link that appears in the upper left under the
    small home icon.

![Run the "Reset Password" task](http://cdn1.o8.io/cdn/farfuture/LVOwjX3qZOlwoyG2LLk683kduMH_q5m6ujOOP6UiZFg/mtime:1335973438/sites/omega8.cc/files/imagecache/lead-image-home/7/Fullscreen-98.jpg "Run the "Reset Password" task")

### Using Drush

If you `ssh` into your Aegir account, you can get the "Log in" link
using drush.

1.  `cd` into a directory for your site. (For example, `sites/foo.com/`)

1.  `drush5 uli`

1.  Copy the link into your browser. This link will log you in to
    the site.

More Information
----------------

### So the Site Owner Doesn't Need to Send the Password?

Correct. You should **never** have the site owner send you a
password. Instead, use this technique to log into the site without
altering the password.

### Can I Log In As A Particular User?

If you want to log in as a particular user, you can add that username
to the `drush5 uli` command. For example:

`drush5 uli "John Doe"`

[ssh]
