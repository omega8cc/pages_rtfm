---
# http://learn.getgrav.org/content/headers
title: BOA-2.4.1 Full Edition
slug: boa-241-full-edition-351
# menu: BOA-2.4.1 Full Edition
date: 08-03-2015
published: true
publish_date: 08-03-2015
# unpublish_date: 08-03-2015
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.4.1 Full Edition, with exciting new features, one new and 12 updated Aegir platforms, 15 new software versions, over 10 other changes, plus over 38 bug fixes. Enjoy!

 
    ### Stable BOA-2.4.1 Release - Full Edition
    ### Date: Sun Mar  8 14:56:51 PDT 2015
    ### Milestone URL: https://github.com/omega8cc/boa/milestones/2.4.1
    
      @=> Includes Aegir Hostmaster 2.x-head with improvements
      @=> Includes Aegir Provision 3.x-head with improvements
      @=> Includes Drush 7.0.0-alpha9 customized for BOA
    
    # Release Notes:
    
      This new BOA release includes one new and 12 updated Aegir platforms,
      8 new features and enhancements, 15 new software versions, 10 other changes,
      plus over 38 bug fixes, with most notable features and changes listed below:
    
      @=> Add duobackboa with /root/.duobackboa.cnf file to run duplicate backups
      @=> Add SSL with TLS/SNI on server with one IP, multiple certificates support
      @=> Add support for Octopus batch migration - see docs/MIGRATE.txt for details
      @=> Allow to use _PHP_GEOS=YES with all PHP versions
    
    # New Octopus platforms:
    
      OpenAid 2.0 ------------------ https://drupal.org/project/openaid
    
    # Updated Octopus platforms:
    
      Commerce 1.33 ---------------- https://drupal.org/project/commerce_kickstart
      Commerce 2.21 ---------------- https://drupal.org/project/commerce_kickstart
      Commons 2.22 ----------------- https://drupal.org/project/commons
      Commons 3.22 ----------------- https://drupal.org/project/commons
      Drupal 8.0.0-b7 -------------- https://drupal.org/drupal-8.0
      Guardr 2.8 ------------------- https://drupal.org/project/guardr
      OpenAtrium 2.32 -------------- https://drupal.org/project/openatrium
      OpenChurch 2.1-b5 ------------ https://drupal.org/project/openchurch
      OpenOutreach 1.16 ------------ https://drupal.org/project/openoutreach
      OpenScholar 3.20.0 ----------- http://theopenscholar.org
      Panopoly 1.18 ---------------- https://drupal.org/project/panopoly
      Recruiter 1.5 ---------------- https://drupal.org/project/recruiter
    
    # New features and enhancements:
    
      * Add compatibility with latest VS beng kernel
      * Add duobackboa with /root/.duobackboa.cnf file to run duplicate backups
      * Add support for multivalued fields in SOLR 4 - pull request #626
      * Add support for mysqladmin proc logging
      * Add support for Octopus batch migration - see docs/MIGRATE.txt for details
      * Add support for scout/mysql monitoring
      * CSF: Add popular ports 222 and 2222 to TCP_OUT by default
      * SSL with TLS/SNI on server with one IP, multiple certificates - fixes #465
    
    # Changes:
    
      * Allow to run automated SQL conversion only weekly
      * Allow to use _PHP_GEOS=YES with all PHP versions
      * Do not send extra nocache cookie on GET requests
      * Drush mini-7-07-03-2015
      * Make barracuda wrapper available on initial install to avoid confusion
      * Nginx: Update for crawlers exceptions list
      * Redis Integration Module: Update to version mod-05-03-2015
      * Remove dependency on legacy Drush 4
      * Use latest Apache Solr Search 6.x-3.x config
      * Use latest Apache Solr Search 7.x-1.x config
    
    # System upgrades:
    
      * Apache Solr 4.9.1
      * cURL 7.41.0 (if installed from sources)
      * Git 2.3.0 (if installed from sources)
      * Jetty 9.2.7.v20150116
      * MariaDB 10.0.17
      * MariaDB 5.5.42
      * Nginx 1.7.10
      * OpenSSL 1.0.2 (if installed from sources)
      * PHP 5.4.38
      * PHP 5.5.22
      * PHP 5.6.6
      * PHP: ionCube loader 4.7.4
      * Ruby 2.2.1
      * Use duplicity 0.7.01 and boto 2.36.0 - fixes #630
      * Vnstat 1.13
    
    # Fixes:
    
      * [provision] False "load on system too heavy" messages - fixes #619
      * [provision] Issue #2350695 - Profile is registered twice, also as a module
      * [provision] Nginx: Remove webform keyword from regex locations - fixes #599
      * Add also manage_ltd_users to the list - fixes #616
      * Avoid installing New Relic with no valid license key provided - fixes #608
      * Do not add no longer used symlink
      * Do not delete backboa while duplicity is running
      * Do not replace any contrib in latest OA - fixes #2420131
      * Do not run D7 core hotfix on already fixed instances
      * Fix for legacy systems autoupdate logic
      * Fix for missing chattr -i on web user update
      * Fix for missing datestamp
      * Fix for too dangerous pdnsd auto-config logic
      * Fix pdnsd restarts procedures - fixes #610
      * Fix permissions for pdnsd if needed
      * Fix variable in autoupboa - pull request #629
      * Force php.ini update
      * Hotfix for cluster instances
      * Hotfix for OpenSSL/cURL versions out of sync
      * Issue #2425963 - Broken slider in Commerce Kickstart 2.21
      * Make sure that @hostmaster alias works after migration
      * Provide a patch for older civicrm versions to make them Drush 7 compatible
      * Randomize backups schedule to avoid issues with AWS limits
      * Remove conflicting pdnsd restarts to avoid race conditions - fixes #610
      * Remove deprecated sysctl options
      * Remove post-install leftovers if needed
      * Single PHP-version installation fails - fixes #598
      * Typo - fixes #539
      * Unable to connect to SOLR on latest head - fixes #623
      * Update meta-installers for new stable
      * Update the upgrade procedure how-to - fixes ##616
      * Use civicrm-4.5.6 compatible with Drush 7
      * Use correct AWS Endpoint when us-east-1 Region is specified
      * Use correct open_basedir for lshell user - fixes #603
      * Use separate loops for symlinks and ghost cleanup
      * Workaround for EntityMalformedException in Open Outreach - fixes #229
      * Workaround for missing interface/lo.pdnsd on legacy systems
      * Workaround for SA-CONTRIB-2015-063 - Webform - Cross Site Scripting


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!