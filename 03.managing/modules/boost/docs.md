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
Using the Boost Module for Caching

The [Boost](https://drupal.org/project/boost) module caches full pages
for **anonymous** visitors only. On our hosting, Boost can be used in
conjuction with other caching systems such as [Speed
Booster](cache-speed-booster)
and [Redis.](cache-redis)

Task: Enable Boost
------------------

Boost is supported in our Nginx server configuration, so you do not
use an `.htaccess` file or need to do any other configuration.

To use Boost, simply:

1.  **Enable** the module as usual, on the "Modules" admin page.

1.  If this is a custom platform in the `~/static` directory, and this
    is
    the first site on the platform for which you have enabled Boost,
    then you must also "Verify" this site in Aegir (see
    "Caution" below).

**** With our built-in platforms, you do not need this extra step.

Task: Disable Boost
-------------------

You can disable Boost like any other module, on the "Modules" admin
page.

To disable Boost for a particular URL on the fly, add `?nocache=1`.
This will also disable [Speed Boost](cache-speed-booster) for that URL.

Caution
-------

### Boost Needs a "cache/" Directory

Boost requires a `cache/` directory in the platform.


(Example: &lt;code&gt;~/static/my-platform-01/&lt;strong&gt;cache&lt;/strong&gt;/&lt;/code&gt;)

This directory is automatically included on all
our [built-in platforms](built-in-platforms).

If you [add a custom platform](add-custom-platform), you can also
trigger
the creation of this directory with correct permissions with these
steps:

1.  Enable the Boost module for one of the sites on this platform.

1.  Run the "Verify" task on this site.

It is important that you use Aegir to create this directory in your
custom platform. You shouldn't create it via FTPS, SFTP, or on the
command
line. If the directory has been copied during the site import
procedure,
you should delete and re-create it via Aegir, as explained above.

References
----------

-   [Using Speed Booster Caching](cache-speed-booster)

-   [How to Disable All Caching](cache-disable-all)

-   [How to Disable CSS and Javascript Caching](cache-disable-css-js)

