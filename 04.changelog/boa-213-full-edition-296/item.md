---
# http://learn.getgrav.org/content/headers
title: BOA-2.1.3 Full Edition
slug: boa-213-full-edition-296
# menu: BOA-2.1.3 Full Edition
date: 21-11-2013
published: true
publish_date: 21-11-2013
# unpublish_date: 21-11-2013
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

 We are happy to release BOA-2.1.3 Full Edition, which includes important security upgrades for Drupal 7 and Pressflow 6 cores, Nginx security upgrade and several other fixes and improvements plus some new features and two updated Platforms, introduced in the last 3 days since previous Edition.

 
    ### Stable BOA-2.1.3 Release - Full Edition
    ### Date: Thu Nov 21 17:55:47 SGT 2013
    ### Includes Aegir 2.x-boa-custom version.
    
    # Release Notes:
    
      This release provides Drupal 7.24.1 and Pressflow 6.29.1 core security upgrade
      for all supported distributions. It also includes two updated platforms and
      several fixes for issues discovered since BOA-2.1.2 released 3 days ago, plus
      some clever improvements to help you automatically optimize all tables daily,
      or even automatically convert tables to-innodb or to-myisam, either per site
      or per platform, or per entire Octopus instance. There is also Purge Cruft
      Machine available to run some spring-cleaning daily with configurable TTL.
    
      Enjoy another super-fast and even more clever BOA Edition!
    
    # Updated Octopus platforms:
    
      ### Drupal 7.24.1
    
      Open Atrium 2.0.9 ------------ http://drupal.org/project/openatrium
      OpenScholar 3.9.3 ------------ http://openscholar.harvard.edu
    
    # New features and enhancements in this release:
    
      * Purge Cruft Machine moved to daily.sh agent and made configurable
        with _DEL_OLD_BACKUPS and _DEL_OLD_TMP per Octopus instance.
    
        If changed to any number greater than "0" it will automatically delete
        backups stored in the /data/disk/U/backups/ directory and in all hosted
        sites backup_migrate directories, during daily cleanup, if created more
        than X days ago, where X is a number of days defined in _DEL_OLD_BACKUPS.
    
        If "0" then this feature is disabled. It can't be configured via INI files,
        so you may need to submit support request if you want to customize this
        option set to 7 days by default on all hosted instances, as per our
        backups policy: https://omega8.cc/backups
    
        The same logic applies to _DEL_OLD_TMP which defines for how long the
        temporary files in all hosted sites files/tmp/ and private/temp/ directories
        are kept before deleting them during running daily maintenance.
    
      * Added sql_conversion_mode variable in the platform and site level INI
        to customize instance-wide mode optionally set via _SQL_CONVERT.
    
        This option allows to activate and/or customize DB tables conversion
        per site, per platform and via _SQL_CONVERT per Octopus instance.
    
        Supported values are: innodb and myisam (lowercase only!)
        Note that this conversion will run daily even if all tables have been
        already converted, so it will run OPTIMIZE on all tables, effectively.
    
        Related Issue #2126471 - Convert DB engine control files to ini format.
    
    # Changes in this release:
    
      * Allow to install unsupported distros only in head, not stable.
      * Contrib update: advagg-7.x-2.3
      * Map drush to drush6 on command line. You can still use drush4 and drush5.
      * New contrib: display_cache
      * New contrib: panels_content_cache
      * Nginx 1.5.7 -- security upgrade.
      * Use dev versions of CDN module with patch for AdvAgg 7 compatibility.
      * Use Drush 5 and 6 head until next release.
    
    # Fixes in this release:
    
      * Always cleanup temp downloads to avoid failed builds due to leftovers.
      * Always fix permissions on contrib on upgrade and in daily.sh agent.
      * Better auto-recovery when broken libcurl is detected.
      * Delete any tar/gz/zip files in modules|themes|libraries daily.
      * Delete dangerous local-allow.info file.
      * Display all active INI variables in HTTP headers on dev URLs.
      * Fix for cron auto-correction.
      * Fix for Feature Server broken due to incorrect context version downloaded.
      * Fix the logic for cURL install from sources.
      * Nginx: Add Access-Control-Allow-Origin header also for static .json
      * Nginx: Protect also .md files in modules|themes|libraries dirs.
      * Issue #2137583 - Permissions on the site directory are broken after running,
        how ironically, the Health Check task.
      * Issue #2138811 - Maintenance agent disables modules from its standard
        turn-off list, even if they are required by other modules, apps or features.
    
    # Known Issues on systems upgraded to initial BOA-2.1.3 release
    
      ==> Updated on Fri Nov 22 21:18:33 SGT 2013 with all fixes applied to stable.
    
      @=> Issues which will trigger `barracuda up-stable system` if discovered:
    
      * PHP: Fix for broken cURL from sources install logic.
      * PHP: Fix for forced rebuild mode if lib curl is broken or updated.
      * Use dummy variable instead of 'true' to avoid breaking the logic.
    
      @=> Issues which will NOT trigger `barracuda up-stable system` if discovered:
    
      * Issue #2141283 - Drush aliases like `drush dbup` no longer work properly.
      * MariaDB 5.5.34 just released.
    
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