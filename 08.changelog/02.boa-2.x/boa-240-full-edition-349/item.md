---
# http://learn.getgrav.org/content/headers
title: BOA-2.4.0 Full Edition
slug: boa-240-full-edition-349
menu: BOA-2.4.0 Full Edition
date: 04-02-2015
published: true
publish_date: 04-02-2015
# unpublish_date: 04-02-2015
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.4.0 Full Edition, with 7 updated Aegir platforms, over 28 new features and enhancements, 12 new software versions, over 36 important changes, plus over 100 bug fixes.

 
    ### Stable BOA-2.4.0 Release - Full Edition
    ### Date: Wed Feb  4 20:30:04 CET 2015
    ### Milestone URL: https://github.com/omega8cc/boa/milestones/2.4.0
    
      @=> Includes Aegir Hostmaster 2.x-head with improvements
      @=> Includes Aegir Provision 3.x-head with improvements
      @=> Includes Drush 7.0.0-alpha8 customized for BOA
    
    # Release Notes:
    
      This new BOA release includes 7 updated Aegir platforms, over 28 new features
      and enhancements, 12 new software versions, over 36 important changes, plus
      over 100 bug fixes, with most notable features and changes listed below:
    
      @=> Added Support for latest Drupal 8.0.0-beta with D8B platform keyword
      @=> Added Support for latest Drupal 8.0.0-dev with D8D platform keyword
      @=> Added Support for latest PHP 5.6
      @=> BOA can auto-detect its fastest download mirror on install, upgrade etc.
      @=> BOA Code Refactoring to make it modular and easier to read (in progress)
      @=> BOA Skynet auto-updates can be turned off with _SKYNET_MODE=OFF
      @=> Cron is run only for live sites with no tmp, temp, dev, test etc keywords
      @=> Force single PHP version with command keyword on install and upgrade
      @=> Introducing Support for HHVM -- see docs/HHVM.txt for details.
      @=> PHP 5.5 is used by default on new installs instead of old 5.3
      @=> PHP-FPM (and HHVM) runs now as a separate, very limited system user
      @=> Removed Support for legacy PHP 5.2
      @=> Sites Names Exceptions and Special Keywords have changed
      @=> The _MODULES_FIX variable is set to NO by default
      @=> The _PERMISSIONS_FIX variable is set to NO by default
      @=> The built-in registry-rebuild on every Verify task is not run by default
      @=> The Dev-Mode works only for site aliases, no longer for main site name
    
      Please read further below for more details.
    
    # Updated Octopus platforms:
    
      aGov 1.6 --------------------- https://drupal.org/project/agov
      Commerce 1.32 (with 1.11) ---- https://drupal.org/project/commerce_kickstart
      Guardr 2.7 ------------------- https://drupal.org/project/guardr
      OpenAtrium 2.26 -------------- https://drupal.org/project/openatrium
      OpenChurch 1.17-b1 ----------- https://drupal.org/project/openchurch
      OpenPublic 1.4 --------------- https://drupal.org/project/openpublic
      Panopoly 1.15 ---------------- https://drupal.org/project/panopoly
    
    # New features and enhancements:
    
      * Add backboa variables to configure full backup cycle and log verbosity.
      * Add Backdrop CMS compatibility in global.inc (experimental)
      * Add Drupal 8 compatibility in global.inc
      * Add Drush Make Local - fixes #332
      * Add safe_cache_form_clear Drush extension by default - fixes #568
      * Add support for writable .aws directory in the web user home.
      * Allow to set _PHP_SINGLE_INSTALL on command line - on install and upgrade.
      * Allow to use both platform specific and ALL keyword in _PLATFORMS_LIST.
      * BOA auto-selects the fastest download mirror on install, upgrade and update.
      * Detect critically low free RAM and forcefully restart services if needed.
      * Detect OOM incidents and forcefully restart services if needed.
      * Improve backboa with AWS connection testing.
      * Install latest D8-dev with D8D keyword specified.
      * Monitor and rotate PHP error logs if too big (over 1 GB).
      * Monitor the number of master PHP-FPM processes and force restart if needed.
      * New 'nodns' option to skip DNS and SMTP checks on the fly.
      * Nginx: Add support for images derivatives with URI shortcuts - fixes #481
      * Nginx: Add support for URI shortcuts for sites in subdirectories.
      * PHP: Add HHVMinfo.
      * PHP: Add support for latest 5.6
      * PHP: Allow to define version to install and use on command line - fixes #536
      * PHP: Disable not used CLI versions if _PHP_SINGLE_INSTALL is defined.
      * PHP: Disable not used FPM and CLI versions.
      * PHP: HHVM experimental support - fixes #443
      * Provide default value for composer_manager_vendor_dir variable - fixes #385
      * Redis: Allow to configure remote IP via _REDIS_LISTEN_MODE /cluster support.
      * Use cron scheduler fast mode (every 10 sec) if /root/.fast.cron.cnf exists.
      * Use Drush Make Local for Hostmaster with download mirrors auto-detection.
    
    # Changes:
    
      * Alter the cron_interval for existing sites to match Aegir default.
      * Change required exceptions keywords to .temporary. and .testing.
      * Dev mode detection and URLs protection - now works only for aliases.
      * Do not display .cnf files contents if _DEBUG_MODE is not set to YES.
      * Do not restart Redis daily if /root/.high_traffic.cnf exists - fixes #533
      * Drush 7 is now used by default instead of Drush 6.
      * Drush: Upgrade to mini-7-02-02-2015
      * Force _TOMCAT_TO_JETTY=YES - fixes #570
      * Hostmaster: Use Drush Make Local instead of downloading contrib with Drush
      * Limit status messages verbosity if _DEBUG_MODE is not set to YES
      * Make it possible to opt-out from BOA Skynet auto-updates - fixes #557
      * Nginx: Block SEOkicks crawler.
      * PHP: Always use by default version 5.5
      * PHP: Disable legacy 5.2 version if installed.
      * PHP: Ignore --with-curlwrappers defined in _PHP_EXTRA_CONF for 5.5 and 5.6
      * PHP: Rebuild to remove --with-curlwrappers unless added in _PHP_EXTRA_CONF
      * PHP: Remove no longer working custom config protection - see #559
      * PHP: Tune FPM defaults for speed and RAM optimization.
      * PHP: Use built-in Zend OPcache in 5.5
      * PHP: Use built-in Zend OPcache in 5.6
      * Redis Integration Module: Update to version mod-14-12-2014
      * Reload system cron hourly.
      * Remove deprecated RC4 from ssl_protocols.
      * Remove the _O_CONTRIB_UP variable/feature.
      * Run cron for 3 sites at once max.
      * Set _MODULES_FIX=NO by default
      * Set _PERMISSIONS_FIX=NO by default
      * Site mode detection and cron protection - cron works only for live sites
      * Split huge BARRACUDA script into lib includes.
      * Switch to special limited system user also in PHP-FPM mode - fixes #551
      * There is no need to update drupalgeddon every 5 minutes.
      * Use 86400 as a default cron_interval to sync with Drupal default.
      * Use MySQLTuner only if _USE_MYSQLTUNER=YES is set in .barracuda.cnf
      * Use provision_civicrm 6.x-2.x directly.
      * Use separate versioning for Aegir extensions download URLs.
      * Run built-in registry-rebuild on Verify only if empty ctrl file
        sites/all/modules/registry-rebuild.ini exists.
    
    # System upgrades:
    
      * cURL 7.40.0 (if installed from sources)
      * Git 2.2.1 (if installed from sources)
      * MariaDB 10.0.16
      * MariaDB 5.5.41
      * MariaDB Galera Cluster 10.0.16
      * Nginx 1.7.9
      * PHP 5.4.37
      * PHP 5.5.21
      * PHP 5.6.5
      * PHP: ionCube loader 4.7.3
      * Redis 2.8.19
      * Ruby 2.2.0
    
    # Fixes:
    
      * Add CONTRIBUTING.txt guidelines.
      * Add in docs/HINTS.txt Helper locations to avoid 404 on legacy images paths.
      * Add still missing updates for migrated instances.
      * Add warning about vCloud Air incompatibility with Drupal.
      * Aliases are wiped out after site rename - fixes #542
      * Allow slower DNS response.
      * Always disable spinner when running boa in-octopus.
      * Avoid broken install on D8 core where sites/all doesn't exist by default.
      * Avoid confusing EXIT: You must specify already installed PHP version.
      * Avoid sed warnings in old stable and legacy modes.
      * Backward compatibility with Drush 6.
      * Block attempts to lookup /etc/passwd via web shell.
      * Check only LANG environment variable in locale test - fixes #584
      * Compare $new_uri with d()->name and not d()->uri in the Site Rename Check.
      * Delete duplicity ghost pid file if older than 2 days.
      * Do not confuse D7 with D8 or Backdrop CMS.
      * Do not force cURL reinstall from packages - fixes #565
      * Do not try to add platforms nodes if no new platform has been installed.
      * Do not update backboa if duplicity is running.
      * Document when to use /root/.fast.cron.cnf
      * Drupal 8 removed drupal_mail()
      * Drupal 8 requires container_yamls defined.
      * Drupal 8 requires read permissions in sites/all
      * Drupal 8 requires trusted_host_patterns defined in settings.php
      * Drupal 8 with $clean_urls=1 should use /cron/ URI.
      * Drush 7 requires composer.
      * Fix and Improve Squeeze to Wheezy upgrade procedure.
      * Fix for $HOME detection if not set for some reason.
      * Fix for Drush aliases protection.
      * Fix for octopus batch upgrade mode.
      * Fix for octopus single upgrade mode.
      * Fix for pdnsd install/update logic.
      * Fix missing symlinks after broken openjdk-6 upgrade.
      * Fix path to PHP-CLI if needed.
      * Fix public IP auto-detection on AWS in Octopus.
      * Fix the logic for aegir/platforms upgrade mode.
      * Fix the logic for TMPDIR set on the fly - fixes #552
      * Fix: LANGUAGE (en_US.UTF-8) is not compatible with LC_ALL (). Disabling it.
      * Force _PHP_MULTI_INSTALL to match defined _PHP_FPM_VERSION on cluster nodes.
      * Force _THIS_DB_HOST=localhost on AWS.
      * HHVM: Add /home/ to open_basedir so access to the .tmp works - fixes #569
      * HHVM: Add workarounds for potential security issues - fixes #443
      * Improve Aegir tasks scheduling and load spikes protection.
      * Improve docs for backboa.
      * Improve pdnsd configuration update by removing non-IP lines early enough.
      * Improve procs monitor.
      * Improve web wrapper.
      * Increase inotify defaults to improve lsyncd support.
      * Issue #2372653: Add --no-autocommit when dumping MySQL tables.
      * Jetty: Detect if running as zombie and force restart if needed.
      * Make sure that AcceptEnv is set in sshd_config.
      * Make sure to never run cron on just cloned site.
      * MariaDB patch is no longer needed.
      * Monitor lsyncd and xinetd if installed and expected to run.
      * Never delete tmp dirs to avoid Drush/PHP segfaults and race conditions.
      * Nginx: Add missing variables in subdirectory config template.
      * Nginx: Fix for D8-specific /cron/ location regex.
      * Nginx: Force clean URLs for Drupal 8.
      * Nginx: Helper locations to avoid 404 on legacy images paths (subdir only)
      * Nginx: Hide X-Drupal-Cache-Tags header.
      * Nginx: Use safe fallback for mysteriously empty $db_port
      * PHP: Avoid version guessing for Octopus when _PHP_SINGLE_INSTALL is used.
      * PHP: Make sure that _PHP_SINGLE_INSTALL takes precedence.
      * PHP: OPcache configuration for Drupal 8 - fixes #419
      * PHP: Re-install libmagickwand-dev to avoid broken extension build.
      * PHP: The fallback version should be detected and not hardcoded.
      * Prevent 'Could not change permissions' warnings with CiviCRM - fixes #523
      * Remove Drupal 8 specific code from settings template used in older Drupal.
      * Remove known sensitive credentials from barracuda upgrade log.
      * Revert "Issue #2313327: Fixed Unknown options for provision-verify."
      * Run agents update on cluster nodes.
      * Run single mirror check - fixes #565
      * RVM: Install also eventmachine-1.0.3
      * Set files paths on D8 install to avoid using system default /tmp.
      * Silence confusing noise - fixes #589
      * Skip auto-update for agents not compatible with older versions.
      * Skip extra SQL connection test on AWS.
      * Standardize platforms version and naming convention.
      * Support for _NGINX_NAXSI is experimental (don't use)
      * Symlinks directories expected by Drush/Aegir in D8 root.
      * Sync defaults for hosting_advanced_cron_default_interval
      * Syntax error - fixes #587
      * Syntax error - fixes #588
      * The _NGINX_FORWARD_SECRECY=YES is ignored on Debian Wheezy - fixes #591
      * The /login suffix is no longer supported in Drupal 8 and results with 404.
      * The backend verify sub-task breaks site import for Drupal 8.
      * Tomcat is not used anymore - see #570
      * Use consistent stderr 2 stdout redirects in grep checks.
      * Use correct _THIS_DB_HOST on master instance.
      * Use correct pid file in procs monitor.
      * Use correct user to run drush test commands.
      * Use extended display mode for messages longer than 200 chars.
      * Use faster mysqldump mode/flags.
      * Use mirror to download complete vendor directory for Drush 7.
      * Use more intuitive PHP keyword naming convention.
      * Use mutatable interface in install_8.inc - fxes #2409085
      * Use recommended releases for views404 and views_accelerator - fixes #578
      * Use release specific o_contrib downloads.
      * Use safe tmp cleanup to avoid race conditions.
      * Where to set _USE_MYSQLTUNER variable - fixes #594


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!