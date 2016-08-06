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
How to Disable all Caching and Aggregation

Caching and aggregation are huge performance boosts, but when you're\
developing your site (especially your theme), they can prevent you\
from seeing your changes.

Quickstart Guide to Disabling Caching
-------------------------------------

If your layout is broken, and you're not sure whether caching is the\
culprit, here are some steps to try, in order of difficulty. Most are\
explained in more detail below.

1.  Add ?nocache=1 to the URL and reload.

1.  Add ?noredis=1 to the URL and reload.

1.  Edit a node or block on the page. This can force the cache to\
    reload.

1.  If the page is a view, check whether you need to disable caching
    for\
    the view.

1.  Purge all Boost's caches and then "disable the
    module"\#disable-boost.\
    The order is very important here.

1.  [Use a .dev. or .devel. alias](#caching-dev) for the site, visit
    the\
    admin Performance page via this alias, and try disabling various\
    caching settings.

**** Drupal 6: `admin/settings/performance`

**** Drupal 7: `admin/config/development/performance`

1.  Use the [AdvAgg module](#use-advagg), or, if you're already using
    it,\
    uninstall and delete it, if you have a copy in `sites/all/modules/`.

If none of these solve your problem, keep reading to investigate\
further.

Overview: Disable Caching So You Can Change Settings
----------------------------------------------------

On a standard Drupal site, you can disable caching and aggregation\
settings on a site's "Performance" administrator page.

However, our hosting can only achieve its high speed by overriding\
this system. By default, \*you cannot change settings on the\
Performance page\*. You will first need to disable certain caching.\
Then you can change the settings on the Performance page.

Note: some caching can only be disabled temporarily. When this caching\
is enabled again, your settings on the Performance page will also be\
overridden.

Task: Disable Caching
---------------------

Here is a full list of all typical settings on the admin Performance\
page. For each setting, we have the default value, and what you have\
to do to change it.

These are the main actions you can take to disable different kinds of\
caching settings:

-   [Use a `.dev.` or `.devel.` alias](#caching-dev)
-   [Disable Redis](#disable-redis)
-   [Disable Speed Booster](#disable-speed-booster)
-   [Disable Boost](#disable-boost)
-   [Use AdvAgg](#use-advagg)

Note which action affects which settings in the charts below.

### Drupal 6 Performance Page Settings

Access this Drupal 6 Performance page at: `/admin/settings/performance`

  --------------------------- --------------------------- ------------------------------------------------------------------------------
  \_. Setting                 \_. Default Value           \_. How to Override
  Caching Mode                Forced as Normal            "Use `.dev.` or `.devel.`":\#caching-dev
  Minimum Cache Lifetime      Forced as none              "Disable Redis":\#disable-redis
  Page Cache Maximum Age      Forced as none              "Disable Redis":\#disable-redis
  Page Compression            Always Forced as Disabled   Cannot be disabled (Nginx)
  Block Cache                 Never Forced                No action needed.
  Optimize CSS Files          Forced Enabled (see note)   [Disable Speed Booster](#disable-speed-booster) and "Boost":\#disable-boost.
  Optimize Javascript Files   Forced Enabled (see note)   [Disable Speed Booster](#disable-speed-booster) and "Boost":\#disable-boost.
  --------------------------- --------------------------- ------------------------------------------------------------------------------

Note: if [AdvAgg 6.x](#use-advagg) is present (even if it's not enabled\
for this site), then both **Optimize CSS Files** and \*Optimize\
Javascript Files\* are Forced *Disabled*. You must [configure
AdvAgg](module-advagg)\
instead.

### Drupal 7 Performance Page Settings

Access the Drupal 7 Performance page at:
`admin/config/development/performance`).

  ---------------------------------- --------------------------- ------------------------------------------
  \_. Setting                        \_. Default Value           \_. How to Override
  Cache Pages For Anonymous Users    Forced Enabled              "Use `.dev.` or `.devel.`":\#caching-dev
  Minimum Cache Lifetime             Forced as none              "Disable Redis":\#disable-redis
  Expiration Of Cached Pages         Forced as none              "Disable Redis":\#disable-redis
  Compress Cached Pages              Always Forced as Disabled   Cannot be disabled (Nginx)
  Aggregate And Compress CSS Files   Forced Enabled              "Use `.dev.` or `.devel.`":\#caching-dev
  Aggregate Javascript Files         Forced Enabled              "Use `.dev.` or `.devel.`":\#caching-dev
  ---------------------------------- --------------------------- ------------------------------------------

<a name="caching-dev">\
h3. Task: Use a ".dev." or ".devel." Alias

#### Overview: The ".dev." or ".devel." Alias

Whenever you access a site with an alias that includes `.dev.` or\
`.devel.`, certain caching and aggregation settings, which are normally\
forced as enabled, can be disabled on the Performance page. See the\
tables above for which settings are affected by this alias.

#### Step-by-Step: Add a ".dev." or ".devel." Alias

1.  In Aegir, click "Sites".

1.  Click your site name. This brings to your site node.

1.  Click "edit".

1.  Add an alias that includes `.dev.` or `.devel.`

**** Note: the alias **must include both periods**.

****\* `bar.dev.foo.com` and `bar.devel.foo.com` will work.

****\* `devel.foo.com` and `dev_foo.com` will **not** work.

****\* The exception is a domain which *begins* with `dev.`; so\
`dev.foo.com` will still work.

1.  Save the node and wait until the Verify task completes.\
    You can now access your site via this alias! Visit the Performance\
    page via this alias to change the desired settings.

The public domain name for this site will *not* be affected. If you\
want to change the behavior for the public site, you will need to try\
one of the other actions, such as disabling Speed Booster.

Using `.dev.` or `.devel.` will *allow* to disable caching, but it does\
not actually disable anything automatically. The one thing it does do\
is set the [TTL](ttl) (cache time) for Speed Booster down to 1 second.\
(Since it uses a cookie, bots are not affected.)

<a name="disable-redis">\
h3. Task: Disable Redis

(copy section from cache-redis once cache-redis is approved)

<a name="disable-speed-booster">\
h3. Task: Disable Speed Booster

(copy section from cache-speed-booster once speed-booster is approved)

<a name="disable-boost">\
h3. Task: Disable Boost

Boost is an ordinary module, and can be disabled on the Modules admin\
page as usual.

You can also disable Boost for any URL on the fly by adding\
`?nocache=1`. This will also disable Speed Booster for that URL.

<a name="use-advagg">\
h3. Task: Use AdvAgg to Disable CSS and Javascript Aggregation

(copy section from module-advagg once module-advagg is approved)

More Information
----------------

### Which Caching is Enabled Automatically?

Our hosting comes with certain caching/aggregation enabled and active\
**automatically**. You can disable these, but only **temporarily**.

-   [Redis caching](cache-redis)
-   [Speed Booster caching](cache-speed-booster)
-   Nginx (web server) caching, which cannot be disabled

### Which Caching is Supported But Not Enabled Automatically?

Our hosting also includes caching/aggregation which is *supported*,\
but not enabled by default. If you have enabled this caching, you may\
need to disable it.

-   [Boost module](module-module), which is included but not enabled.
-   [AdvAgg module](module-advagg), which is supported but must
    be downloaded.

\[redis\]https://drupal.org/project/redis\
\[module-advagg\]\
\[module-boost\]\
\[cache-disable-all\]\
\[cache-disable-css-js\]\
\[cache-speed-booster\]\
\[cache-redis\]\
\[redis\]https://drupal.org/project/redis\
\[import-your-site\]
