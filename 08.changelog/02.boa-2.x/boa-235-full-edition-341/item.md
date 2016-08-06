---
# http://learn.getgrav.org/content/headers
title: BOA-2.3.5 Full Edition
slug: boa-235-full-edition-341
menu: BOA-2.3.5 Full Edition
date: 15-10-2014
published: true
publish_date: 15-10-2014
# unpublish_date: 15-10-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.3.5 Full Edition, with all Drupal 7 platforms updated to include latest Drupal core security upgrade and many other fixes and improvements accumulated in almost 3 weeks since previous release.

 
    ### Stable BOA-2.3.5 Release - Full Edition
    ### Date: Wed Oct 15 16:28:25 PDT 2014
    ### Includes Aegir 2.1 with improvements
    ### Latest hotfix added on: Thu Oct 16 08:55:02 PDT 2014
    
    # Release Notes:
    
      This new BOA release includes important updates and bug fixes.
    
      * All new Drupal 7 platforms received Drupal core security upgrade.
        For details please read: https://www.drupal.org/SA-CORE-2014-005
    
      * All existing Drupal 7 built-in platforms will receive a hot-fix for
        this known vulnerability: https://www.drupal.org/SA-CORE-2014-005
        once you will run 'barracuda up-stable' command on your server.
        This procedure is automated on hosted and managed Aegir at Omega8.cc
    
      * Your custom D7 platforms created in the ~/static directory tree
        will be checked in the next 12 hours after the upgrade, and if you
        have not applied this patch yet, it will be applied automatically
        for you - but only if there is at least one active site present
        in the given custom D7 platform. Note that while this procedure is
        automated on hosted and managed Aegir at Omega8.cc, on self-hosted
        BOA systems it will work only if you will set _PERMISSIONS_FIX=YES
        in /root/.barracuda.cnf (default is NO)
    
      We recommend that you upgrade your D7 sites using safe workflow:
    
        https://omega8.cc/your-drupal-site-upgrade-safe-workflow-298
    
    # Updated Octopus platforms:
    
      aGov 1.5 --------------------- https://drupal.org/project/agov
      Commerce 1.31 ---------------- https://drupal.org/project/commerce_kickstart
      Commerce 2.19 ---------------- https://drupal.org/project/commerce_kickstart
      ERPAL 2.1 -------------------- https://drupal.org/project/erpal
      Guardr 1.14 ------------------ https://drupal.org/project/guardr
      Open Atrium 2.22 ------------- https://drupal.org/project/openatrium
      Open Outreach 1.12 ----------- https://drupal.org/project/openoutreach
      OpenPublic 1.2 --------------- https://drupal.org/project/openpublic
      Panopoly 1.12 ---------------- https://drupal.org/project/panopoly
      Recruiter 1.3 ---------------- https://drupal.org/project/recruiter
    
    # New features and enhancements in this release:
    
      * Explain that Solr self-provisioning works only if _MODULES_FIX=YES is set.
      * Reverify all sites daily if /root/.force.sites.verify.cnf ctrl file exists
        and _PERMISSIONS_FIX=YES is set in /root/.barracuda.cnf (default is NO)
    
    # Changes in this release:
    
      * Security: Remove support for SSLv3 due to POODLE vulnerability.
      * Disable Redis in Hostmaster until we will fix the Views based pages/blocks.
      * Disable site_readonly for non-dev sites by default.
      * Drush: Upgrade command line version 6 to mini-6-04-10-2014
      * Enable AllowUserFXP in Pure-FTPd config by default.
      * Remove support for already deprecated non-LTS Ubuntu versions.
      * Run manage_ip_auth_access only once per minute.
      * The INI variable redis_flush_forced_mode is enabled by default (again).
      * Use sysklogd instead of rsyslog on Ubuntu.
    
    # System upgrades in this release:
    
      * MariaDB 5.5.40
      * Nginx 1.7.6
      * OpenSSH 6.7p1 (if installed from sources)
      * OpenSSL 1.0.1j (if installed from sources) - security upgrade.
      * PHP 5.5.18
      * PHPRedis: master-03-10-2014
    
    # Fixes in this release:
    
      * Add auto-detection of Legacy Ruby patch level update on old systems.
      * Add cleanup for ghost/broken sites dirs leftovers.
      * Add missing cleanup for backup_migrate leftovers.
      * Always cleanup pid files on exit/abort.
      * Apply patch for SA-CORE-2014-005 in all shared D7 cores/built-in platforms.
      * Compass Tools: Install 1.9.3 ffi expected by older themes.
      * Fix db_port entry in all vhosts hourly.
      * Fix for broken erpal-7.x-2.0-7.31.1
      * Fix for broken site level drushrc.php file.
      * Fix for false alarm caused by ghost sites leftovers.
      * Fix for incorrect hash filtering on systems with OpenSSL built from sources.
      * Fix locales: Numerous fixes and improvements -- thanks ar-jan!
      * Fix typo in REVISIONS.
      * Force site Verify via frontend if drushrc.php has been fixed.
      * Issue #435 - SQL: Remove deprecated table_cache +update table_open_cache
      * Issue #440 - Improve innodb_buffer_pool_size calculation and add 10%
      * Issue #441 - New Relic is not disabled after removing newrelic.info file.
      * Issue #442 - Skip locked/fpmcheck if /root/.high_traffic.cnf exists.
      * Issue #444 - PHP: Remove useless sed replacement in pool.d/www{*}.conf
      * Issue #445 - Remote Import: update 6.x-2.x branch for Aegir 2.x and Drush 6
      * Issue #447 - Export LANG, LANGUAGE and all LC_ environment variables.
      * Issue #447 - Improve locales consistency.
      * Issue #447 - Set default LC_CTYPE and LC_COLLATE environment variables.
      * Issue #447 - Simplify locales configuration on Ubuntu.
      * Issue #448 - Enforce locale settings by configuring defaults.
      * Issue #452 - PHP build is broken with latest MariaDB 5.5.40
      * Make sure that db_port is never empty and defaults to 3306.
      * Make sure that firewall monitoring scripts never run simultaneously.
      * Make sure that standard caching is enabled in hostmaster.
      * Pause hostmaster tasks when RVM install for any user is running.
      * PHP: Do not run rebuilds if not needed.
      * PHP: Fix for broken upgrade logic on libcurl or libssl packages upgrade.
      * Remove acquia_connector from latest Commons to avoid broken installs.
      * Remove all legacy gems and re-install RVM/Ruby for root from scratch.
      * Remove legacy replacement to avoid converting symlinked includes into files.
      * SQL: Use correct defaults if MySQLTuner test failed.
      * Workaround for Drupal flood using 127.0.0.1 for all requests behind proxy.


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!