---
# http://learn.getgrav.org/content/headers
title: BOA-2.2.7 Full Edition
slug: boa-227-full-edition-324
# menu: BOA-2.2.7 Full Edition
date: 16-07-2014
published: true
publish_date: 16-07-2014
# unpublish_date: 16-07-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.2.7 Full Edition, which includes some nice new features, improvements, bug fixes, one new and five updated Octopus platforms with latest Drupal core.

 
    ### Stable BOA-2.2.7 Release - Full Edition
    ### Date: Thu Jul 17 03:11:47 CEST 2014
    ### Includes Aegir 2.x-boa-custom version.
    ### Latest hotfix added on: Fri Jul 18 18:21:40 CDT 2014
    
    # Release Notes:
    
      This release includes some nice new features, improvements, bug fixes, one
      new Octopus platform, five (5) updated Octopus platforms, along with latest
      Drupal core security upgrades for all supported platforms.
    
      NOTE: Since the first Edition in the BOA-2.3.x series is not ready for release
      yet, and new Drupal core has been released today to fix security issues,
      we have decided to make it available to everyone and release yet another
      stable BOA-2.2.x series Edition.
    
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
    
    # New Octopus platforms:
    
      OpenPublic 1.0-b23 ----------- https://drupal.org/project/openpublic
    
    # Updated Octopus platforms:
    
      Commerce 1.27 ---------------- https://drupal.org/project/commerce_kickstart
      Commons 3.15 ----------------- https://drupal.org/project/commons
      ERPAL 2.0-b4 ----------------- https://drupal.org/project/erpal
      Guardr 1.9 ------------------- https://drupal.org/project/guardr
      Open Deals 1.33 -------------- https://drupal.org/project/opendeals
    
    # New features and enhancements in this release:
    
      * Add early auto-repair procedure if Provision is missing for any reason.
      * Add support for Debian Squeeze LTS updates.
      * Add support for Debian Squeeze Stable Proposed Updates.
      * Add views_accelerator in all D7 platforms by default via o_contrib bundle.
      * Issue #307 - Support for Compass Tools via RVM with local user gems.
      * Make $conf['cache'] configurable via disable_drupal_page_cache INI variable.
    
    # Changes in this release:
    
      * Nginx: Send Boost compatible Cache-Control headers also with Speed Booster.
    
       This is to mimic Drupal core behaviour when full-page cache is disabled,
       even if it is not really disabled via disable_drupal_page_cache INI variable.
       Note that Speed Booster continues to ignore Cache-Control headers sent by
       Drupal backend, as before, to force its own TTL set via INI variable:
       speed_booster_anon_cache_ttl or in the custom local.settings.php code.
    
      * Add css_emimage to hostmaster makefile to remove dependency on o_contrib.
      * Do not upgrade existing o_contrib, only add new if missing in old platforms.
      * Drush: Upgrade command line version 6 to mini-6-16-07-2014
      * Limited Shell configuration update.
      * Nginx: Do not log HTTPS redirects.
      * PHP: AutoRemove 5.2 from _PHP_MULTI_INSTALL if no instance is using it.
      * Prefer dash if available.
      * Redis Integration Module: Update to version mod-10-07-2014
      * The ?nocache=1 in the URL should also force $conf['cache'] = 0; on the fly.
      * Update lfd default configuration.
    
    # System upgrades in this release:
    
      * cURL 7.37.1 (if installed from sources)
      * Nginx 1.7.3
      * PHP 5.4.30
      * PHP 5.5.14
      * PHPRedis: master-06-07-2014
      * Redis 2.8.13
    
    # Fixes in this release:
    
      * Authorized IPs detection - it should ignore serial/remote console logins.
      * BND --- Bind9 DNS Server (available on Debian only).
      * Clear packages cache more aggressively to avoid issues during OS upgrades.
      * Configure RVM env properly if installed in the user home directory.
      * Contrib update: filefield-6.x-3.13
      * Disable redis integration during hostmaster upgrade.
      * Do not allow known bots to activate nocache and noredis URLs behaviour.
      * Do not use css_emimage in hostmaster to avoid broken upgrades.
      * Fix for o_contrib update logic.
      * Fix for possible permissions problem with redis log file.
      * Fix incorrect version in the permissions fix.
      * Fix legacy test logic to allow head instances to upgrade to another 2.2.x
      * Fix regex in procs monitor.
      * Fix the check for legacy systems on upgrade.
      * Force keyring reinstall if reported as broken.
      * Issue #316 - Octopus upgrade fails because of missing cd $_ROOT/.drush/sys
      * Issue #319 - XTRAS_LIST settings are being overwritten (Ubuntu).
      * Issue #320 - Compass Tools available on Squeeze, Wheezy, Precise and Trusty.
      * Issue #324 - HTTPS results in redirect loop on AWS due to ignored _MY_OWNIP.
      * Issue #328 - The /bin/sh symlink modified daily causes false lfd alarm.
      * Make it clear that we recommend and support Debian 64bit.
      * Make sure that redis and cache_backport are available for hostmaster.
      * Purge no longer used jdk leftovers.
      * Readme improvements.
      * Remove no longer needed tmp chown -R
      * Remove no longer used /data/src directory.
      * Remove remote_import if found if the wrong directory.
      * Sanitize logs lines before analyzing them.
      * The list of platforms symbols can be in a single line or one per line.
      * There is no need to force SHELL in the websh wrapper.
      * Update nginx documentation URL.
      * Use static ftp.debian.org instead of unreliable http.debian.net mirrors.
    


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!