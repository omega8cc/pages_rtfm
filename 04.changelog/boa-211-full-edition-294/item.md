---
# http://learn.getgrav.org/content/headers
title: BOA-2.1.1 Full Edition
slug: boa-211-full-edition-294
# menu: BOA-2.1.1 Full Edition
date: 09-11-2013
published: true
publish_date: 09-11-2013
# unpublish_date: 09-11-2013
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

 We are happy to release BOA-2.1.1 Full Edition, which includes eight updated Platforms, some important features, plus several fixes and improvements introduced in the last 7 days since previous Edition.

 
    ### Stable BOA-2.1.1 Release - Full Edition
    ### Date: Sat Nov  9 17:00:00 EST 2013
    ### Includes Aegir 2.x-boa-custom version.
    
    # Release Notes:
    
      There are some important bug fixes in this release, along with changes
      to the Auto-(En|Dis)able agent, explained in greater detail in embedded docs
      included in platform specific INI file template.
    
      Note that the system agent doesn't modify any existing and active INI file,
      so updated docs are included only in the updated each morning INI templates:
      default.boa_platform_control.ini and default.boa_site_control.ini
    
      You can find both INI templates also online at: https://omega8.cc/node/293
    
      We have also added some docs to help you if you experience any issues
      with cached, Views based pages and panels: https://omega8.cc/node/292
    
      Note also that since BOA-2.1.0 all D6 based sites are forced to use PHP 5.3.27
      on hosted and managed Aegir instances, even if they were previously configured
      to use deprecated, insecure, unstable and outdated PHP 5.2 for D6 based sites.
    
      This means that if you are using either too old D6 core (older than 6.28.x)
      some features will stop working, namely imagecache, /update.php and any
      feature which depends on contrib modules not yet compatible with PHP 5.3
    
      We have allowed to use PHP 5.2 for too long, to give enough time (in years)
      to upgrade to latest Pressflow 6.x version and we no longer can extend
      this allowance, for obvious security and systems stability reasons.
    
      Furthermore, sticking with PHP 5.2 would not allow us to use latest Aegir 2.x
      version (BOA still includes a bit older Aegir 2.x for backward compatibility),
      since newer Aegir versions need newer Drush (BOA still uses ancient Drush 4.6)
      and newer Drush requires newer PHP version.
    
      It is even more important because Drupal 8 will not run on older PHP nor Drush
      older than 7.x, so there is basically no choice other than make all your sites
      compatible with PHP 5.3, or you will miss all future BOA system upgrades.
    
      Now even PHP 5.3 is officially in the EOL (End-of-Live) phase, with only
      security fixes expected, but also only until July 2014 and then it will be
      completely deprecated, so we will have to switch to modern PHP 5.5, first
      introduced as an option, later this year.
    
      Upgrading to latest Pressflow 6.x is *very* easy. Just add all contrib modules
      you are using in your outdated 6.x platform to the latest Pressflow 6.x
      platform we provide by default, reverify the new platform, clone the site
      in the old platform, migrate the cloned copy to the new platform and if
      everything works fine, migrate also your live site. It will take less than
      15 minutes and there is absolutely no excuse to not upgrade.
    
      If you experience issues with your site due to the old core used on now forced
      PHP 5.3, we can temporarily revert it to PHP 5.2 for the last time, but it is
      really a bad idea. Much better idea is to find those 15 minutes and upgrade
      your site, so we could continue to provide future upgrades and new amazing
      features also for your Aegir instance.
    
      Enjoy new, shiny BOA Edition!
    
    # Updated Octopus platforms:
    
      ### Drupal 7.23.3
    
      Open Atrium 2.0.4 ------------ http://drupal.org/project/openatrium
      Open Deals 1.31 -------------- http://drupal.org/project/opendeals
      OpenBlog 1.0-a3 -------------- http://drupal.org/project/openblog
      Recruiter 1.1.2 -------------- http://drupal.org/project/recruiter
      Spark 1.0-a10 ---------------- http://drupal.org/project/spark
      Totem 1.1.2 ------------------ http://drupal.org/project/totem
    
      ### Pressflow 6.28.3
    
      Commons 2.13.2 --------------- http://drupal.org/project/commons
      Open Atrium 1.7.2 ------------ http://drupal.org/project/openatrium
    
    # New features and enhancements in this release:
    
      * Document all system-level control files in docs/ctrl/system.ctrl
      * Fast Redis lock implementation is now enabled by default for D6 and D7.
      * Nginx: Add NAXSI (Nginx Anti XSS & SQL Injection) WAF as an option.
      * Use 100% static downloads in stable to remove dependency on github and d.o
      * Use extended connection check procedure before exit 1.
      * Use reliable Redis UP check via PING/PONG instead of pid file check.
    
    # Updated o_contrib modules:
    
      * Contrib update: httprl-6.x-1.13
      * Contrib update: httprl-7.x-1.13
      * Contrib update: redis-7.x-2.3
      * Contrib update: views_cache_bully-6.x-3.x
      * Contrib update: views_cache_bully-7.x-3.x
      * Contrib update: views_content_cache-7.x-3.0-alpha3
    
    # Changes in this release:
    
      * Introducing Pressflow 6.28.3 to include fix for #2130865
      * Updated INI docs for views_cache_bully and views_content_cache.
      * ProsePoint moved to unsupported.
    
      * Private files mode in D7 requires allow_private_file_downloads = TRUE in
        boa_site_control.ini or boa_platform_control.ini and is disabled by default.
    
      * Do not enable views_cache_bully and views_content_cache, unless special
        control files exist and related variables in the platform specific INI
        are not set to TRUE.
    
      * Auto-Disable views_cache_bully on sites with commerce module enabled, but
        allow to override it with ~/static/control/enable_views_cache_bully.info
        and views_cache_bully_dont_enable = FALSE
    
    # Fixes in this release:
    
      * All-in-One Site Health Check in Aegir not displayed for non-uid=1 users.
      * Always prepare shared D6 and D7 cores.
      * Always remove www. from the Redis cache key prefix.
      * Better check for not yet updated Octopus instances in a batch upgrade mode.
      * Check if ctools is enabled before attempting to enable views_content_cache.
      * Do not force HEAD on Precise.
      * Fix for /root/.upstart.cnf consistency.
      * Fix for PATH in aegir.sh
      * Fix still too aggressive procs monitoring.
      * Fix the check_if_required() logic in the Auto-Disable agent.
      * Improve all cURL based downloads with auto-continue mode.
      * Issue #1980250 - Fix for broken cache_page bin in Redis integration module.
      * Issue #2127237 - NewRelic: Unable to initialize module on Debian Wheezy.
      * Issue #2128233 - Rsyslog is still installed and consumes all CPU on OpenVZ.
      * Issue #2128819 - Better exceptions in too aggressive process monitoring.
      * Make sure to never set any HTTP headers or redirects in the backend.
      * Nginx: Do not use separate location for /images/ URI shortcut.
      * Nginx: Fix for regression in "Rewrite for legacy requests with /index.php".
      * Nginx: Fix the logic for restricted access to /authorize.php and /update.php
      * Nginx: Map URI shortcuts early to avoid overrides in other locations.
      * Remove rsyslog on VZ, if installed.
      * Restore backward compatibility with IP and not wildcard based vhosts.
      * Use silent upgrade mode in _LENNY_TO_SQUEEZE and _SQUEEZE_TO_WHEEZY.
      * Issue #2127329 - AdvAgg (D6 version) presence in o_contrib should not
        auto-disable standard aggregation, unless the module is enabled.
    
    # Known Issues on systems upgraded to initial BOA-2.1.1 release
    
      ==> Updated on Tue Nov 12 14:44:16 EST 2013 with all fixes applied to stable.
    
      * Fast Redis lock may cause problems on node edit, with temporary error
        saying that the node was changed by "another user", because current
        implementation was not multisite-aware enough.
    
      * Views Cache Bully module, if enabled after upgrade to BOA-2.1.0, may break
        the cart and checkout on sites using Ubercart, and should be disabled
        automatically like it is done for Commerce based sites since BOA-2.1.1
    
      * The version of Redis integration module included: 7.x-2.3 causes warnings
        for D6 sites, visible either on dev URLs or on command line and may break
        some advanced Views configurations if custom caching is not yet enabled.
        It may also break menu updates due to not aggressive enough cache clear
        policy for cache_menu bin.
    
      * Permissions set daily on the civicrm.settings.php file are too restrictive
        and since provision_civicrm extension does not make this file writable
        before attempting to re-create it, as it should, all tasks on CiviCRM
        enabled sites fail.
    
      * Permissions on sites/all/{modules,theme,libraries} on newly added, empty
        platforms with no sites created yet, so not included in the running daily
        permissions fix, are initially not group writable, as they should be.
    
      * The check_if_required procedure in the running daily maintenance agent to
        detect if the module is required by any other module or feature or by
        installation profile, is 6 (six) slower than it should be and never disables
        devel module properly.
    
      * The running daily maintenance agent does not disable files checks for
        Drupal for Facebook (fb) and Domain Access modules as it should in the
        platform level INI file, unless those modules are detected.
    
    # HotFix for known post-upgrade issues
    
      Run the boa-fix-upgrade script when logged in as system root:
    
      $ cd;rm -f boa-fix-upgrade.sh.txt*
      $ wget -q -U iCab http://files.aegir.cc/update/boa-fix-upgrade.sh.txt
      $ bash boa-fix-upgrade.sh.txt
    
      This script is updated once there is any new regression or bug discovered,
      so it is safe and recommended to run it again if the list of known issues
      have been updated.
    
      You can also run another upgrade with "barracuda up-stable system" command,
      followed by "octopus up-stable all both log" since all fixes have been applied
      to current stable as well, but boa-fix-upgrade script is faster than running
      complete upgrade again.
    


 You can read full changelog as always at: http://bit.ly/newboa

Enjoy!