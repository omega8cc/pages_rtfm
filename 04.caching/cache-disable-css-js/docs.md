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

How to Disable CSS and Javascript Aggregation

h2. Problem: Your Layout Keeps Breaking

Does the layout on your Drupal site break whenever you clear the
cache? Or, do you edit your CSS or Javascript files, clear the cache,
and not see any changes?

h2. Solution: Disable CSS/Javascript Aggregation

The problem may be CSS and Javascript _aggregation_. To increase
performance, CSS and Javascript files are by default _aggregated_ into
single files with unique names. The pages of your Drupal site only
load these aggregated files, rather than the source files (like
@styles.css@).

If you disable aggregation, then the pages should load your source
files without any problem.

Disabling aggregation also causes a performance hit, so *permanently
disabling aggregation is not allowed* in our hosted environment.

However, for debugging and theme development, you can follow these
steps to disable aggregation on the fly or temporarily.

h3. How to Disable Aggregation On The Fly With a ".dev." Alias

If you just need to disable aggregation for your own personal
development, simply:

# Create an alias for the site that includes @.dev.@ or @.devel.@

** Example: @bar.dev.foo.com@

** Make sure you include both periods in @.dev.@ or @.devel.@
   (The exception is a domain which _begins_ with @dev.@; so,
   @dev.foo.com@ will still work.)

# Through this alias, go to the "Performance" admin page and disable
  CSS and Javascript aggregation.

** Drupal 6: @admin/settings/performance@
** Drupal 7: @admin/config/development/performance@

Now aggregation will be disabled when you browse the site through this
@.dev.@ or @.devel.@ alias.

You can use this private @.dev.@ alias for as long as you like.
Aggregation will still be enabled when the public accesses this site
through its main domain name.

You should be able to develop your theme with the alias, and then
eventually see your changes get aggregated in the public version.
How long it takes depends on your caching settings,
especially "Speed Booster":cache-speed-booster.

h3. How to Disable Aggregation On Your Actual Site Temporarily

If your live site is mysteriously broken, you may need to *temporarily*
disable aggregation until the problematic theme or module is fixed
by adding these settings to @local.settings.php@:

# Create an empty control file at:
   @sites/foo.com/modules/local-allow.info@

# In Aegir, run the "Reset password" task on your site. Wait until the
  task finishes. Now @local.settings.php@ is writable.

# Add these lines to @local.settings.php@:   
   @unset($conf['preprocess_css']);@   
   @unset($conf['preprocess_js']);@

# Go to the Performance page. Now you can disable CSS and Javascript aggregation.

# Disabling aggregation *permanently* is *not allowed* in our hosted
  environment. Go now and solve your issue. Then continue with these
  steps to return the system to normal.

# Remove or comment the two lines you added to @local.settings.php@.
  Save. Aggregation is now enabled again.

# Make sure your website loads properly. A typo in
  @local.settings.php@ can break your entire site.

# In Aegir, run "Verify" on your site. This restores
  @local.settings.php@ to its safe, unwritable state.

h2. Caution

Disabling aggregation like this when you have "AdvAgg 7.x":module-advagg
enabled may cause some warnings, since "AdvAgg 7.x":module-advagg
expects the Drupal aggregation to be _enabled_ in order for this module to function properly.
For "AdvAgg 6.x":module-advagg, it is not a problem, since this version expects
the Drupal aggregation to be _disabled_.

h2. References

* "How to Edit settings.php on Aegir":edit-settings-php

* "How to Disable All Caching":cache-disable-all

* "Using the AdvAgg Module.":module-advagg

* "Using Speed Booster Caching":cache-speed-booster.
