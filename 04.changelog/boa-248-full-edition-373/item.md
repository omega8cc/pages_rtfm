---
# http://learn.getgrav.org/content/headers
title: BOA-2.4.8 Full Edition
slug: boa-248-full-edition-373
# menu: BOA-2.4.8 Full Edition
date: 20-02-2016
published: true
publish_date: 20-02-2016
# unpublish_date: 20-02-2016
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.4.8 Full Edition, which includes several important system upgrades and  
 bug fixes, plus platforms with latest Drupal cores. Enjoy!

 
    ### Stable BOA-2.4.8 Release - Full Edition
    ### Date: Sat Feb 20 11:28:05 GMT 2016
    ### Milestone URL: https://github.com/omega8cc/boa/milestones/2.4.8
    ### Latest hotfix added on: Mon Feb 22 18:28:51 GMT 2016
    
      @=> Includes Aegir Hostmaster 2.x-head with improvements
      @=> Includes Aegir Provision 3.x-head with improvements
      @=> Includes Drush 7 customized for BOA
    
    # Release Notes:
    
      This BOA release includes several important system upgrades and bug fixes,
      with most notable features and changes listed below.
    
      @=> Debian 8 Jessie is fully supported, but includes only PHP 5.5 and 5.6
    
      @=> All supported Aegir platforms have been updated with latest Drupal cores
    
      @=> Even if deprecated PHP versions are still included in this release,
          any Octopus instance running PHP older than 5.5 will not be able to
          receive upgrade to BOA-2.4.8, as announced before -- Please switch your
          Octopus to PHP 5.6 or at least 5.5 to be able to upgrade not only
          the Barracuda system part of BOA, but also Octopus Satellite --
          The how-to can be found at: https://omega8.cc/node/330
    
      @=> Drupal 8 support for custom platforms in the ~/static directory tree
          will be included, along with Drush 8 and PHP 7 in the *upcoming*
          BOA-3.0.0 release: https://github.com/omega8cc/boa/milestones/3.0.0
          Note: BOA will not include built-in Drupal 8 platforms until Drupal 8
          will support symlinks in the codebase, like all previous core versions
    
      @=> What are BOA plans for Drupal 6 support after February 24th, 2016?
    
          We will support Drupal/Pressflow 6 in all new releases, as long as
          available PHP versions will allow to use it (we run our own Pressflow 6
          based site on PHP 5.6 for many months with zero issues). For more details
          please check: https://github.com/omega8cc/boa/issues/824
    
    # Changes:
    
      * Add "boa info" and 'boa info more' helper command
      * Add branch support in the boa wrapper
      * Allow to force re-install with /root/.force.reinstall.cnf present
      * Allow to run existing Octopus 2.4 on the upcoming Barracuda 3.0
      * Deny Octopus upgrade unless it is running on a compatible PHP version 5.5+
      * Full backboa backups are scheduled on Sunday, unless custom _AWS_FLC is set
      * Full duobackboa backups will run on Saturday, unless custom _AWS_FLC is set
      * Make base nice configurable via _B_NICE variable
      * Nginx: Sync htaccess level protection with Drupal core
      * Nginx: Update map $http_user_agent $is_crawler
      * Only instance already running 2.4.8 can upgrade to upcoming 3.0.0
      * Remove no longer supported T1lib in PHP
      * Remove support for deprecated OS versions -- fixes #802
      * Replace in-legacy and up-legacy with version specific commands
      * Revert "Issue #2377819: Gzipping backups suppresses file permissions errors"
      * Run minimal modules en/dis procedure on Wednesday and full on Saturday
      * Skip legacy PHP 5.3 and 5.4 on Jessie
      * Support for Debian 8 Jessie -- fixes #702
      * The _MODULES_FIX variable is set to YES by default
      * The _PERMISSIONS_FIX variable is set to YES by default -- fixes #593
    
    # System upgrades:
    
      * Git 2.7.0 (if installed from sources)
      * MariaDB 10.0.24
      * MariaDB 5.5.48
      * Nginx 1.9.11
      * OpenSSH 7.1p2 (if installed from sources)
      * OpenSSL 1.0.2f (used only in custom built Nginx)
      * PHP 5.5.32
      * PHP 5.6.18
      * PHP: Imagick 3.3.0
      * Redis 3.0.7
      * Ruby 2.3.0
    
    # Fixes:
    
      * Add duobackboa docs
      * Add missing libs in Jessie
      * Allow to install a specific PHP version on a local install -- fixes #848
      * Allow to run upgrade from not really 3.x HEAD to 2.4.8
      * Automate /root/.force.reinstall.cnf and improve docs
      * Disable Octopus 3.x specific version check (tmp) for 2.4.8
      * Disable spinner on Jessie
      * Do not force rebuild on systems installed with 2.4.8
      * Do not kill long running php-fpm childs
      * Do not run the old D7 core fix on newer BOA versions -- fixes #842
      * Do not wait for simple sed replacements -- fixes #838
      * Fix a typo in some locCnf variable calls -- fixes #854
      * Fix for ignored boa_platform_control.ini
      * Fix for MariaDB version check
      * Fix for not working S3 bucket connection test
      * Fix for process.max and pm.max_children
      * Fix for undefined locCnf variable in BOND - fixes #748
      * Fix the logic in mysql_proc_kill()
      * Fix too aggressive Jetty monitoring
      * Force clean rsyslog/sysklogd restart if required
      * Force rebuild for affected services built from sources -- CVE-2015-7547
      * Improve backup sub-tasks randomized schedule
      * Improve initial install how-to with screen
      * Locales check should not be used with screen session -- fixes #871
      * Nginx: Remove duplicate $args on redirects
      * Nginx: Workaround for broken autocomplete
      * Remove dependency on _MODULES_FIX=YES -- fixes #592
      * Remove no longer used _SSL_FROM_SOURCES logic
      * Remove systemd on Debian Jessie -- fixes #840
      * Restart syslog hourly
      * Run drush cache cleanup only once per account
      * Speed up backup tasks by removing extra conn_test
      * Speed up backup tasks by running extended cleanup and reporting weekly
      * Speed up initial setup procedure
      * Sync wait randomizer max value
      * Upgrade wkhtmltopdf and wkhtmltoimage to 0.12.3 - fixes #858
      * Use date %u day of week (1..7); 1 is Monday
      * Whitelist missing upload progress path


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!