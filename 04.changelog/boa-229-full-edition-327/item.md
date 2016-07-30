---
# http://learn.getgrav.org/content/headers
title: BOA-2.2.9 Full Edition
slug: boa-229-full-edition-327
# menu: BOA-2.2.9 Full Edition
date: 06-08-2014
published: true
publish_date: 06-08-2014
# unpublish_date: 06-08-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

 We are happy to release BOA-2.2.9 Full Edition, which includes updated versions of all supported Drupal platforms, plus some changes, improvements, bug fixes and updated Octopus platforms.

 
    ### Stable BOA-2.2.9 Release - Full Edition
    ### Date: Wed Aug  6 17:08:10 PDT 2014
    ### Includes Aegir 2.x-boa-custom version.
    ### Latest hotfix added on: Fri Aug 15 09:37:04 PDT 2014
    
    # Release Notes:
    
      This release includes updated versions of all supported Drupal platforms to
      provide latest Drupal 7 and Pressflow 6 core, plus some changes, improvements,
      bug fixes, and many updated Octopus platforms.
    
      NOTE: Since the first Edition in the BOA-2.3.x series is not ready for release
      yet, and new Drupal core has been released to fix security issues, followed
      by yet another release to fix serious regressions, followed by yet another
      security release, we have decided to make it available to everyone and release
      yet another stable BOA-2.2.x Edition.
    
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
    
      aGov 1.2 --------------------- https://drupal.org/project/agov
      Commerce 1.29 ---------------- https://drupal.org/project/commerce_kickstart
      Commerce 2.17 ---------------- https://drupal.org/project/commerce_kickstart
      Commons 2.20 ----------------- https://drupal.org/project/commons
      Commons 3.17 ----------------- https://drupal.org/project/commons
      ERPAL 2.0-b5 ----------------- https://drupal.org/project/erpal
      Guardr 1.11 ------------------ https://drupal.org/project/guardr
      Open Atrium 2.21 ------------- https://drupal.org/project/openatrium
      Open Outreach 1.10 ----------- https://drupal.org/project/openoutreach
      OpenPublic 1.0-rc4 ----------- https://drupal.org/project/openpublic
      Panopoly 1.11 ---------------- https://drupal.org/project/panopoly
      Restaurant 1.0-b2 ------------ https://drupal.org/project/restaurant
    
    # New features and enhancements in this release:
    
      * Allow to define always disabled modules via _MODULES_FORCE variable.
      * Eldir: Add subtle 3D and round some edges.
      * Eldir: Improve spacing and hide useless headers.
      * Fix permissions on sites/all/{modules,libraries,themes} on Platform Verify.
      * Make firewall management faster with randomized schedule.
      * Merge pull request #362 from pricejn2/imageapi-optimize-binaries
      * RVM: Add exceptions for gems which can't be installed in Limited Shell.
      * Shell: Compass Tools: Allow to access guard.
      * Shell: Improve config to better support advanced Drush commands over SSH.
    
    # Changes in this release:
    
      * Drush: Upgrade command line version 6 to mini-6-14-08-2014
      * Nginx: Add DBot to is_crawler list.
      * Remove no longer supported NodeStream distro.
      * Run complete modules-dis-list weekly (Saturday) and basic list daily.
    
    # System upgrades in this release:
    
      * MariaDB 10.0.13
      * MariaDB 5.5.39
      * Nginx 1.7.4
      * OpenSSL 1.0.1i (if installed from sources)
      * PHP: ionCube loader 4.6.1
      * PHP: Zend OPcache master-30-07-2014
    
    # Fixes in this release:
    
      * Add cleanup for .tmp in sub-accounts.
      * Add cleanup for drush-backups leftovers.
      * Add cleanup for various /var/backups/* leftovers.
      * Add daily auto-cleanup for ghost vhosts, platforms and drush aliases.
      * Add exception for symlinked /data/all
      * Add hint for HTTPS-only mode forced in local.settings.php
      * Allow to clear drush cache without directory restrictions.
      * Avoid "Is a directory" noise in the log.
      * Commons 2.20 has changed its profile name from drupal_commons to commons.
      * Do not modify site_footer on hostmaster upgrade.
      * Do not rename the legacy Commons profile name.
      * Fix -mtime expected values.
      * Fix cleanup for .restore vhost leftovers.
      * Fix cleanup for drush aliases in sub-accounts.
      * Fix for unreliable _IS_OLD check on Octopus instances upgrade.
      * Fix Nginx monitor to respect all whitelisted POST requests in both modes.
      * Fix permissions on sites/all/{modules,libraries,themes} globally.
      * Fix weird typo in global.inc
      * Improve cleanup for empty platforms directories.
      * Improve RVM cleanup.
      * Issue #2278847 - Derivatives (Drupal Commons) can't be created on install.
      * Issue #334 - Backported provision_civicrm #1485920
      * Issue #334 - Delete the civicrm_class_loader variable after deploying.
      * Issue #334 - Install civicrm in any location (sites/ profiles + contrib).
      * Issue #360 - Exclude special --CDN vhosts from daily cleanup.
      * Make sure that /keys subdirectory exists to avoid active platforms cleanup.
      * Make sure that local IPs are never blocked by mistake.
      * Never touch websh wrapper to avoid high load because of redirect loop.
      * Nginx: Detected $device is not used in Boost config, only in Speed Booster.
      * Nginx: Fix limreq also for some really old vhosts.
      * Nginx: Modify only vhosts known as included in the protected mode.
      * Remove /var/run/daily-fix.pid if exists when it shouldn't.
      * Remove debugging mode in old codebases cleanup.
      * Remove no longer needed/used contrib updates.
      * Restore default websh wrapper symlink as fast as possible.
      * Run manage_ltd_users every 3 minutes instead of every minute.
      * Simplify colorbox-1.3.18 download.
      * Simplify colorbox-1.5.13 download.
      * Uninstall css_emimage only on hostmaster upgrade.
      * Update and improve docs/FAQ.txt
      * Update regex for exceptions in Nginx monitoring.


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!