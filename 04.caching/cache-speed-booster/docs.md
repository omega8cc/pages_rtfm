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

Using Speed Booster Caching

h2. What Is Speed Booster Caching?

"Speed Booster" is not a Drupal module, but our special, system-level
configuration. Speed Booster works with any version of Drupal. It is
enabled by default.

Speed Booster caches full pages, both for anonymous visitors and for
logged in users. Each logged-in user gets a separate cache.

h2. Tasks: Working With Speed Booster

h3. How to Disable Speed Booster

h4. How to Disable Speed Booster on Any URL

You can disable the Speed Booster cache on any URL, on demand, by
adding @?nocache=1@ at the end.

For example, to disable Speed Booster caching for
 @http://foo.com/node/1@, browse to: @http://foo.com/node/1?nocache=1@

This will also disable "Boost":module-boost, if it is enabled, for
that URL.

h4. When is Speed Booster Automatically Disabled?

Speed Booster is also *automatically disabled* for certain pages:
@user/*@, @admin/*@, all HTTPS requests.

Speed Booster is also disabled for 15 seconds after any POST request.
This includes any form submission, even for anonymous visitors.

h4. How to Reduce Speed Booster to 1 Second With ".dev."

By default, Speed Booster is set to be valid ("TTL":ttl) for:

* 10 seconds for normal visitors (both anonymous and logged in)
* 24 hours for known bots

These values are hardcoded.

However, if the domain for the site includes @.dev.@ or @.devel.@,
the TTL is lowered to *1 second* (but not for known bots).

You can create a @.dev.@ alias for your site by editing the site node
in Aegir.

Note: both periods in @.dev.@ or @.devel.@ are required. You can use
@bar.dev.foo.com@, but not @devel.foo.com@ or @dev-foo.com@.  The
exception is a domain which _begins_ with @dev.@;
so, @dev.foo.com@ will still work.

Speed Booster will continue to work normally when the site is accessed
through the live domain name.

h4. How to Disable Speed Booster Completely (and Temporarily)

If you need to force a 1-second TTL for the public domain name, which will
effectively disable Speed Booster (the 1-second TTL serves as a minimum
required for active DoS-protection), you will need to edit @local.settings.php@.
This file is not writable by default, but these steps will temporarily
unlock it for editing.

# Create an empty control file at:
   @sites/foo.com/modules/local-allow.info@

# In Aegir, run the "Reset password" task on your site. Wait until the
  task finishes. Now @local.settings.php@ is writable.

# Set a site-wide 1-second TTL, by adding this line to
  @local.settings.php@: @header('X-Accel-Expires: 1');@

# You can also use this conditionally, per URL. For example,
  to lower the TTL only for the site's homepage, use:
  @if (preg_match("/^\/$/", $_SERVER['REQUEST_URI'])) {@
  @   header('X-Accel-Expires: 1');@
  @}@

# Disabling the Speed Booster cache TTL *permanently* is *not allowed*
  in our hosted environment. Go now and solve your issue.
  Then continue with these steps to return the system to normal.

# Remove or comment the @X-Accel-Expires@ line(s) in
  @local.settings.php@. Save. Speed Booster is now enabled again.

# Make sure your website loads properly. A typo in
  @local.settings.php@ can break your entire site.

# In Aegir, run "Verify" on your site. This restores
  @local.settings.php@ to its safe, unwritable state.

h3. How to Enable ESI Microcaching

"ESI microcaching":http://groups.drupal.org/node/197478 allows you to
use a separate microcache for ESI/SSI includes, with its own TTL,
which is set by default to 15 seconds. While Speed Booster caches the rest
of the page separately, these small, included bits can be used to deliver
parts of the page dynamically even if the main Speed Booster cache TTL
is set to 1 hour or longer.

An example is a personalized message like "Logged in as _johndoe_".
Instead of rebuilding the entire page for this user, only _this
message_ is rebuilt. ESI microcaching offers a huge performance boost.

The "ESI module":http://drupal.org/project/esi is included in all
built-in 6.x platforms. However, you will need to enable and configure
this module. Please consult the "module
documentation":http://drupal.org/project/esi for details.

h3. How to Force Different Cache TTL Values

You can set the Speed Booster cache to last _longer_ for anonymous
visitors. You can set this TTL for the entire platform, or set it
separately for each site.

You set this TTL using specially named "control files". These files
are empty. You just need to create the correct filename in the correct
location.

h4. To force a 15-minute cache TTL:

* platform-wide: @sites/all/modules/nginx_cache_quarter.info@
* per site: @sites/foo.com/modules/nginx_cache_quarter.info@

h4. To force a 1-hour cache TTL:

* platform-wide: @sites/all/modules/nginx_cache_hour.info@
* per site: @sites/foo.com/modules/nginx_cache_hour.info@

h4. To force a 24-hour cache TTL, use:

* platform wide: @sites/all/modules/nginx_cache_day.info@
* per site: @sites/foo.com/modules/nginx_cache_day.info@

These settings will not override the cache for logged in users. They
are only for anonymous visitors.

To avoid a broken CSS layout with these longer caches,
"use the AdvAgg module":module-advagg.

h2. More Information

h3. Does Speed Booster Cache Mobile Devices Separately?

Yes. Speed Booster supports separate caches per mobile device. It
is safe to use separate themes or content for mobile devices.

We use simple logic to determine the kind of device, and there are separate
cache bins for @mobile-tablet@, @mobile-smart@ and @mobile-other@.
"Review the code here.":http://bit.ly/wYz6PG

You can access this special variable value set by Nginx also in
your Drupal code (module or theme) via @$_SERVER['USER_DEVICE']@

h2. References

* "ESI module":http://drupal.org/project/esi

* "How to Edit settings.php on Aegir":edit-settings-php

* "How to Disable All Caching":cache-disable-all

* "How to Disable CSS and Javascript Caching":cache-disable-css-js

[advagg]http://drupal.org/project/advagg
[ttl]https://en.wikipedia.org/wiki/Time_to_live
[module-advagg]
[module-boost]
[cache-disable-all]
[cache-disable-css-js]
