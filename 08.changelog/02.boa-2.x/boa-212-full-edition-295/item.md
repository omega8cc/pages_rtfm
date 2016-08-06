---
title: BOA-2.1.2 Full Edition
slug: boa-212-full-edition-295
menu: BOA-2.1.2 Full Edition
date: 17-11-2013
published: true
publish_date: 17-11-2013
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.1.2 Full Edition, which includes many fixes and improvements plus some new features and one updated Platform, introduced in the last 7 days since previous Edition.

 
    ### Stable BOA-2.1.2 Release - Full Edition
    ### Date: Mon Nov 18 00:03:30 SGT 2013
    ### Includes Aegir 2.x-boa-custom version.
    
    # Release Notes:
    
      This is primarily a bug-fix release and you should read release notes and
      also the changelog for both BOA-2.1.1 and BOA-2.1.0 for a context, especially
      if you are upgrading from BOA-2.0.9 or older release (we have tested upgrades
      from as old Editions as BOA-2.0.1, released on Dec 28 07:00:00 EST 2011).
    
      This Edition includes fixes for all Known Issues on systems already upgraded
      to initial BOA-2.1.1 release, plus some extra improvements and one updated
      platform (Managing News).
    
      Important new features include ability to use either legacy (default) or
      modern (highly recommended) version of Redis integration module.
    
      The reason we don't enable the modern version by default is that it may need
      some testing before using it on a complex Drupal sites. The modern version
      of Redis integration module comes with some great new features which allow
      you to configure flush mode per cache bin, with three modes available.
    
      Please refer to the module README for more information on all available
      advanced flush modes: http://bit.ly/1drmi35
    
      It also comes with super-fast lock backend, which can be enabled only when
      you are using the modern version, but still needs more improvements, so we
      auto-configure some exceptions on the fly, when it is used, to avoid known
      issues, as reported in the queue: https://drupal.org/node/2135545
    
      Please read also INI docs to understand how it works, and how to improve
      performance by enabling and tuning these settings: http://bit.ly/1bwfZZj
    
      Enjoy!
    
    
    # Updated Octopus platforms:
    
      ### Pressflow 6.28.3
    
      Managing News 1.2.4 ---------- http://drupal.org/project/managingnews
    
    # New features and enhancements in this release:
    
      * Redis: Modern integration module 7.x-2.5 with latest fixes from #2135545
        is available as an option with new INI variable: redis_use_modern
    
      * Redis: New option redis_flush_forced_mode to better control flush modes
        when redis_use_modern = TRUE
    
      * Add example for custom Speed Booster cache TTL configuration in the optional
        override.global.inc file. It can be used also in local.settings.php file.
    
      * Add detection and auto-config for the allow_private_file_downloads variable.
      * Issue #1978066 - Add _RESERVED_RAM variable for "reserved" memory.
      * Map all old_short_name profiles relations in the Aegir Provision directly.
    
    # Updated Aegir modules or extensions:
    
      * Newer aegir_custom_settings 6.x-2.3 with site clone added for client role.
      * Newer registry_rebuild 7.x-2.1 with fixed critical bug - see: #2130905
    
    # Changes in this release:
    
      * Auto-Disable views_cache_bully also when Ubercart is enabled.
      * Do not delete testing profile, we need it for acquia->testing upgrade path.
      * Do not map old_short_name on the Octopus level, it is moved to Provision.
      * Make ACTIVE INI files comments-free to never confuse them with templates.
      * Make the fix for known Feeds problem global, not just ManagingNews specific.
      * PHP: 5.4.22 and 5.5.6 as an option (for testing only).
      * PHP: Use latest (master) phpredis_new by default.
      * Redis: Default integration module version reverted to pre-7.x-2.0 release.
      * Redis: Force rebuild on system upgrade to update also Redis config.
      * Redis: Make redis_lock_enable available only when redis_use_modern = TRUE
      * Set opcache.revalidate_freq to 5 sec only on non-dev URLs by default.
      * Switch Ubercart 3 to use D7 Minimal instead if Standard to fix upgrade path.
      * Update prev release notes to explain importance of using latest Pressflow 6.
    
    # Fixes in this release:
    
      * Always fix permissions on contrib on upgrade and in daily.sh agent.
      * Avoid files checks for Drupal for Facebook and Domain Access by default.
      * Better auto-recovery when broken libcurl is detected.
      * Fix for cron auto-correction.
      * Fix for post-upgrade permissions issues affecting modules|themes|libraries.
      * Fix for too restrictive permissions in /data/all/000/*
      * Fix regression in the logic for dev URLs detection and auto-configuration.
      * Fix the forced contrib upgrade logic.
      * Fix the logic for cURL install from sources.
      * Improve procs monitoring agent with better whitelisting.
      * Improve sanitize_string() filtering to avoid issues with strong passwords.
      * Issue #1860706 - Native, unified support also for D6 lock backend.
      * Issue #2023895 - Do not kill java, only jetty and tomcat procs when needed.
      * Issue #2105477 - Allowed gem commands need custom aliases in lshell.
      * Issue #2134329 - Going from 2.0.9 to 2.1.1 does not update platforms.
      * Issue #2135545 - Lock Backend freezes the site on cache clear.
      * Issue #2136413 - Use -H to force correct HOME environment variable.
      * Issue #2136413 - Use sudo to avoid lshell protection in DB auto-conversion.
      * Make sure that /usr/local/bin is in the PATH.
      * Make the check_if_required test in daily.sh six (6) times faster.
      * Nginx: Fix too restrictive access policy for Aegir specific /hosting URI.
      * Redis: Add some debugging on dev URLs to make sure permissions are correct.
      * Redis: Added prefix support for lock backend.
      * Redis: Disable persistent mode to never use on-disk storage, see #2135545
      * Redis: Do not enable tcp-keepalive or weird things may happen, see #2135545
      * Redis: Exclude some bins to avoid issues with lock support, see #2135545
      * Redis: Missing default values on variable_get() calls causing D6 break.
      * Redis: Update docs and naming convention for modern integration module.
      * Silence cURL test in meta-installers.
      * Sync randpass with sanitize_string().
      * Set less restrictive permissions on civicrm.settings.php since
        provision_civicrm does not make the file writable temporarily as it should.
    
    # Known Issues on systems upgraded to initial BOA-2.1.2 release
    
      ==> Updated on Thu Nov 21 01:28:23 SGT 2013 with all fixes applied to stable.
    
      * Feature Server platform is broken since BOA-2.1.0 due to incorrect context
        module version downloaded via makefile. This bug affects only some instances
        upgraded to head and not stable, but since in the first 24 hours after
        BOA-2.1.2 release our static downloads were still out of sync on two of
        our mirrors, it is safe to assume that you should run the HotFix via
        boa-fix-upgrade.sh.txt anyway.
    
      * There is regression introduced in the maintenance agent logic, which
        results with dependency check effectively ignored. This may cause various
        disastrous effects, like disabling all modules chained via feature or
        via apps module, because apps module requires update module, which is
        normally disabled. While any feature which requires dblog or update module
        enabled is considered as a serious developer error and should be avoided,
        we have to respect all dependencies defined to never break any site by
        forcefully disabling modules.
    
      * Part of the Site Health Check task (the `drush6 status-report` command)
        breaks permissions on the site directory, which blocks any further tasks
        like Clone, Migrate and Backup. This regression was introduced in the
        BOA-2.1.0 release.
    
    # HotFix for known post-upgrade issues
    
      Run the boa-fix-upgrade script when logged in as system root:
    
      $ cd;rm -f boa-fix-upgrade.sh.txt*
      $ wget -q -U iCab http://files.aegir.cc/update/boa-fix-upgrade.sh.txt
      $ bash boa-fix-upgrade.sh.txt
    
      This script is updated once there is any new regression or bug discovered,
      so it is safe and recommended to run it again if the list of known issues
      have been updated. Note that this script will detect and fix all Octopus
      instances on your system at once.
    


 You can read full changelog as always at: http://bit.ly/newboa

Enjoy!