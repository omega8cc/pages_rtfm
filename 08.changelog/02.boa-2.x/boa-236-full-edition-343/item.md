---
# http://learn.getgrav.org/content/headers
title: BOA-2.3.6 Full Edition
slug: boa-236-full-edition-343
menu: BOA-2.3.6 Full Edition
date: 16-11-2014
published: true
publish_date: 16-11-2014
# unpublish_date: 16-11-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.3.6 Full Edition, with all Drupal 7 platforms updated to include latest Drupal core and many fixes and improvements accumulated in almost 5 weeks since previous release.

 
    ### Stable BOA-2.3.6 Release - Full Edition
    ### Date: Mon Nov 17 08:11:17 SGT 2014
    ### Includes Aegir 2.x-head with improvements
    
    # Release Notes:
    
      This new BOA release includes updated versions of all supported Drupal
      platforms to provide latest Drupal 7.33 core, plus great new features,
      improvements and bug fixes.
    
      We recommend that you upgrade your D7 sites using this safe workflow:
    
        https://omega8.cc/your-drupal-site-upgrade-safe-workflow-298
    
      For up-to-date information on #Drupageddon please check:
    
        https://omega8.cc/drupageddon-psa-2014-003-342
    
    #-### Support for automated, encrypted, daily backups to Amazon S3
    
      * This new feature is available on self-hosted BOA and hosted Power Engines.
      * Note that provided 'backboa' tool uses symmetric password-only encryption.
      * You can configure AWS Region you prefer to use and Backup Rotation policy.
    
      It will archive all directories required to restore your data (sites files,
      databases archives, Nginx configuration and more) on a freshly installed BOA:
    
        /etc /var/aegir /var/www /home /data
    
      It will start to run nightly at 2:08 AM (server time) only once you will add
      five required _AWS_* variables in the /root/.barracuda.cnf file and run the
      special command 'backboa install' while logged in as root.
    
      To restore any file from backups created with 'backboa' tool, you can use
      the same script on the same or any other BOA server.
    
      Please read docs/BACKUPS.txt at https://github.com/omega8cc/boa for details.
    
    # Updated Octopus platforms:
    
      Commons 3.19 ----------------- https://drupal.org/project/commons
      Open Atrium 2.24 ------------- https://drupal.org/project/openatrium
      Open Deals 1.35 -------------- https://drupal.org/project/opendeals
      OpenChurch 1.15 -------------- https://drupal.org/project/openchurch
      OpenChurch 2.0-b2 ------------ https://drupal.org/project/openchurch
      OpenScholar 3.16.0 ----------- http://theopenscholar.org
      Panopoly 1.13 ---------------- https://drupal.org/project/panopoly
      Restaurant 1.0-b10 ----------- https://drupal.org/project/restaurant
      Ubercart 2.14 ---------------- https://drupal.org/project/ubercart
      Ubercart 3.8 ----------------- https://drupal.org/project/ubercart
    
    # New features and enhancements in this release:
    
      * Add support for automated, encrypted, daily backups to Amazon S3.
      * Automatic shutdown for sites with known #Drupageddon users/roles added.
      * Drush drupalgeddon extension added in all accounts.
      * Make _STRONG_PASSWORDS length configurable: 8-128, YES (32), NO (8).
      * Support for web and db clusters with MariaDB Galera (work in progress).
      * Apply SA-CORE-2014-005 hot-fix daily everywhere, also on BOA (any version)
        servers left on the auto-pilot.
    
    # Changes in this release:
    
      * Do not force site_readonly to be disabled on non-dev sites.
      * Ignore disabled sites in daily monitoring and healing procedures.
      * Remove support for abandoned Managing News distro.
      * Remove support for abandoned Open Atrium 6.x distro.
      * Remove support for abandoned Spark distro.
      * Remove support for abandoned Totem distro.
      * Set _PERMISSIONS_FIX=YES by default, so important fixes can be applied.
      * Update BOA wrappers hourly.
    
    # System upgrades in this release:
    
      * cURL 7.39.0 (if installed from sources)
      * Drush: Upgrade command line version 6 to mini-6-30-10-2014
      * Nginx 1.7.7
      * PHP 5.4.35
      * PHP 5.5.19
      * PHP: Zend OPcache master-08-11-2014
    
    # Fixes in this release:
    
      * Add scout user if _SCOUT_KEY is not empty or cron entry exists.
      * Always escape dots in preg_replace() to not truncate www. by mistake.
      * Check if directory tree exists before running extended checks/fixes.
      * Clear drush cache directly before running hostmaster-migrate.
      * Disable scout if installed and enable later.
      * Do not export LC_CTYPE on initial install.
      * Do not use Redis on provision-save.
      * Fix for edge case when incorrect permissions were set in custom platform.
      * Fix for openatrium-7.x-2.22-7.32.1
      * Fix for site_readonly mode in migrated instances.
      * Force setting to avoid issues with not expected to work RVM self-update.
      * Hint for Apache Solr Attachments and Java path possible confusion.
      * Improve web wrapper filtering.
      * Issue #2163979 - Check if field_info_field_map() is available.
      * Issue #2373923 - HTTPS and aliases redirection problem with Nginx.
      * Issue #438 - PHP: Remove support for 5.5 built-in Zend OPcache.
      * Issue #452 - PHP build could be broken also with MariaDB newer than 5.5.40
      * Issue #456 - Aliases redirection: problems with AdvAgg paths.
      * Issue #457 - Aliases redirection: 404 file not found for resources.
      * Issue #461 - Remote Import needs Drush strict=0 mode.
      * Issue #463 - The yajl-ruby gem needs native binaries building.
      * Issue #480 - Normalize /etc/hosts to avoid FQDN mapped to 127.0.1.1
      * Issue #490 - Nginx: Block semalt botnet.
      * Issue #496 - RVM 1.26.0 introduces signed releases (rvm: not found error).
      * Make sure that hostmaster site usage is not counted.
      * Move DB GRANTS setup for master instance to the correct level.
      * Move redis server daily restart to daily.sh agent.
      * Nginx: Fail if required db creds are empty to never create a broken vhost.
      * Remove hardcoded DNS for files.aegir.cc
      * Strict Permissions on All Binaries are default, not optional.
      * There is no point in running MySQLTuner on initial install.
      * Whitelist mysql command for overssh in lshell.


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!