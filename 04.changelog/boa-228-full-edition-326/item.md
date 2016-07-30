---
# http://learn.getgrav.org/content/headers
title: BOA-2.2.8 Full Edition
slug: boa-228-full-edition-326
# menu: BOA-2.2.8 Full Edition
date: 26-07-2014
published: true
publish_date: 26-07-2014
# unpublish_date: 26-07-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

 We are happy to release BOA-2.2.8 Full Edition, which includes updated versions of all supported Drupal platforms, plus some changes, improvements, bug fixes and updated Octopus platforms.

 
    ### Stable BOA-2.2.8 Release - Full Edition
    ### Date: Sat Jul 26 15:31:29 PDT 2014
    ### Includes Aegir 2.x-boa-custom version.
    ### Latest hotfix added on: Tue Aug  5 14:47:17 PDT 2014
    
    # Release Notes:
    
      This release includes updated versions of all supported Drupal platforms to
      provide latest Drupal 7 and Pressflow 6 core, plus some changes, improvements,
      bug fixes, and six (6) updated Octopus platforms.
    
      NOTE: Since the first Edition in the BOA-2.3.x series is not ready for release
      yet, and new Drupal core has been released to fix security issues, followed by
      yet another release to fix serious regressions, we have decided to make it
      available to everyone and release yet another stable BOA-2.2.x Edition.
    
      IMPORTANT! This is the last Edition in the 2.2.x series, which marks the end
      of Drupal 5, PHP 5.2 and Drush 4 support. Next Edition will open 2.3.x series,
      which will allow us to provide newer Aegir version with built-in Drush 6
      support, sites in subdirectories, and many Aegir User Interface improvements.
    
      If you still host any Drupal 5 sites or you are using PHP 5.2 for D6 sites,
      you will not be able to upgrade to the next 2.3.x Edition and you will have to
      stay on the 'legacy' BOA 2.2.x version, which will receive only system
      security upgrades, but no further feature nor bugfix releases.
    
      This also means that from now on the 'legacy' 2.2.x version will no longer
      receive Drupal core upgrades, even if there will be security core releases.
    
      It is time to upgrade away from Drupal 5 and away from PHP 5.2, if still used.
    
    # Updated Octopus platforms:
    
      Commerce 1.28 ---------------- https://drupal.org/project/commerce_kickstart
      Commerce 2.16 ---------------- https://drupal.org/project/commerce_kickstart
      Commons 3.16 ----------------- https://drupal.org/project/commons
      Open Outreach 1.8 ------------ https://drupal.org/project/openoutreach
      OpenBlog 1.0-v3 -------------- https://drupal.org/project/openblog
      Panopoly 1.8 ----------------- https://drupal.org/project/panopoly
    
    # New features and enhancements in this release:
    
      * Allow to force OpenSSL etc. re-install with _SSL_FORCE_REINSTALL=YES
      * Auto-Move no longer used shared codebases to /var/backups/codebases-cleanup
    
    # Changes in this release:
    
      * Drush: Upgrade command line version 6 to mini-6-29-07-2014
      * Issue #334 - Update provision_civicrm version - code by ixiam - thanks!
      * Redis Integration Module: Update to version mod-21-07-2014
      * Uninstall css_emimage in hostmaster to avoid broken upgrades.
      * Update for Contrib [F]orce[D]isabled modules list.
      * Use more aggressive defaults for _PURGE_BACKUPS and _PURGE_TMP if not set.
    
    # System upgrades in this release:
    
      * PHP 5.4.31
      * PHP 5.5.15
    
    # Fixes in this release:
    
      * Add auto-cleanup for civimail ghost leftovers.
      * Add cleanup drush aliases in the main SSH account properly.
      * Add cleanup for RVM archives and logs.
      * Fix for default value on hot fix update.
      * Fix for dev regression - it shouldn't set $conf['cache'] on valid dev URLs.
      * Fix the logic for custom _DEL_OLD_EMPTY_PLATFORMS defaults.
      * Issue #333 - Update BOA changelog URL shortcut.
      * Nginx: Automate SPDY test to determine if OpenSSL re-install is required.
      * Nginx: Silence access log for already protected /civicrm admin requests.
      * Remove special one-time variables if set, once used.
      * RVM: Install OS compatible Ruby version + various related adjustments.
      * Silence useless noise in the log.
      * Sync firewall limits.


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!