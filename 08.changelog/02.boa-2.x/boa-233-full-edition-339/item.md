---
# http://learn.getgrav.org/content/headers
title: BOA-2.3.3 Full Edition
slug: boa-233-full-edition-339
menu: BOA-2.3.3 Full Edition
date: 27-09-2014
published: true
publish_date: 27-09-2014
# unpublish_date: 27-09-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.3.3 Full Edition, which includes latest Aegir 2.1 enhanced version with new features, including sites in subdirectories, self-managed Solr 4 cores, easy to use New Relic integration, plus many changes, improvements and bug fixes.

 
    ### Stable BOA-2.3.3 Release - Full Edition
    ### Date: Sat Sep 27 01:25:46 PDT 2014
    ### Includes Aegir 2.1 with improvements
    
    # Release Notes:
    
      This BOA Edition includes important fixes to address some issues discovered
      after BOA-2.3.1 release. Please read also the release notes for BOA-2.3.1
      further below before running the upgrade!
    
    #-### Important details on CiviCRM versions compatibility and profiles support
    
      * All BOA-2.3.x Editions fully support latest CiviCRM 4.5.0 for Drupal 7.
      * CiviCRM for Drupal 6 is not supported because of known CiviCRM issues.
      * CiviCRM support for Drupal 7 works great when added in sites/all/modules
      * CiviCRM support for Drupal 7 also works when added in profiles/foo/modules
        but no CiviCRM cron is currently managed until this known issue is fixed,
        therefore BOA-2.3.3 will check all platforms on the Octopus instance and if
        it will detect any with CiviCRM added in the installation profile directory
        tree, it will refuse to upgrade such instance to not break things for those
        using currently not fully supported CiviCRM codebase structure.
    
    # New Octopus platforms:
    
      OpenChurch 2.0-b1 ------------ https://drupal.org/project/openchurch
    
    # Updated Octopus platforms:
    
      ERPAL 2.0 -------------------- https://drupal.org/project/erpal
      Guardr 1.13 ------------------ https://drupal.org/project/guardr
      Open Outreach 1.11 ----------- https://drupal.org/project/openoutreach
      OpenChurch 1.14 -------------- https://drupal.org/project/openchurch
      OpenPublic 1.0-rc5 ----------- https://drupal.org/project/openpublic
      OpenScholar 3.15.1 ----------- http://theopenscholar.org
    
    # New features and enhancements in this release:
    
      * Add makefiles for CiviCRM 4.4.7
      * Add makefiles for CiviCRM 4.5.0
    
    # Changes in this release:
    
      * Drush: Upgrade command line version 6 to mini-6-27-09-2014
      * Restart SSH hourly.
      * The INI variable redis_flush_forced_mode is now disabled by default.
      * Use aegir_custom_settings-6.x-3.11
      * Use Provision CiviCRM boa-2.3.3-dev
    
    # System upgrades in this release:
    
      * MariaDB 10.0.14
      * Nginx 1.7.5
      * PHP 5.4.33
      * PHP 5.5.17
      * PHPRedis: master-02-09-2014
      * Redis 2.8.17
    
    # Fixes in this release:
    
      * Add extra cleanup for Drush related caches.
      * Always respect _SSH_PORT if set.
      * Always start cron before aborting on error.
      * Do not add duplicate cron entry for runner.sh
      * Do not allow system only upgrades if Master Instance is still on 2.2.x
      * Do not disable _DNS_SETUP_TEST
      * Enable path_alias_cache by default also in the hostmaster site.
      * Fix for broken pdnsd configuration if wrong IPs are detected.
      * Fix for insufficient permissions on files/civicrm/ConfigAndLog
      * Fix for insufficient permissions on files/civicrm/custom
      * Fix for insufficient permissions on files/civicrm/dynamic
      * Fix for missing cron entry for Scout, if _SCOUT_KEY is not empty.
      * Fix the not working procedure to revert hostmaster features.
      * Force problematic gems install to add them on accounts with enabled RVM.
      * Fox for Java version for Jetty 9 on newer systems.
      * Hardcode files.aegir.cc DNS entry.
      * Improve docs/ctrl/system.ctrl readability.
      * Install openjdk on CI instances by default.
      * Issue #411 - Unable to update Octopus Instance - Reports PHP on 5.2
      * Issue #423 - Make sure that innodb_buffer_pool_size is not smaller than 64M
      * Issue #424 - Update mysqltuner.pl to support MariaDB 10.0
      * Make sure that lsb-release is installed properly.
      * Make the check_civicrm_compatibility more reliable to avoid false alarms.
      * New Relic not enabled if no custom ~/static/control/{fpm|cli}.info exists.
      * Nginx: Auto-Switch to wildcard all vhosts existing in the Master Instance.
      * Nginx: Avoid any downtime on upgrade by using www53.fpm.socket temporarily.
      * Nginx: Convert all config templates to wildcard mode in legacy instances.
      * Nginx: Convert all Octopus vhosts to wildcard mode on Barracuda upgrade.
      * Nginx: Convert config to use PHP 5.2 if the instance still depends on it.
      * Nginx: Delete ghost, outdated or broken config includes in all instances.
      * Nginx: Delete ghost, outdated or broken vhosts in all instances.
      * Nginx: Force special vhosts access rules rebuild hourly.
      * Nginx: Improve wildcard conversion procedure on some really old instances.
      * Purge all ghost delete tasks before running hostmaster-migrate / upgrade.
      * Purge Drush related caches cleanly when needed.
      * Recreate possibly broken vhosts.
      * Remove duplicate cron entry for runner.sh to avoid critical system load.
      * Remove legacy replacement to not convert config symlinks into regular files.
      * Run check_civicrm_compatibility only on upgrade.
      * Single feature revert may not be enough.
      * Update contrib in Open Atrium D7 to maintain upgrade path.
      * Update cron defaults and remove legacy code.
      * Update default SSL Wildcard Nginx Proxy to use wildcard listen mode.
      * Use strict regex in vhosts listen mode conversion to not break ports.
    


Please check also complete BOA-2.3.1 changelog at: https://omega8.cc/boa-231-full-edition-333

You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!