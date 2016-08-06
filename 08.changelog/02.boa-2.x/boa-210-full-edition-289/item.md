---
# http://learn.getgrav.org/content/headers
title: BOA-2.1.0 Full Edition
slug: boa-210-full-edition-289
menu: BOA-2.1.0 Full Edition
date: 02-11-2013
published: true
publish_date: 02-11-2013
# unpublish_date: 02-11-2013
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

We are happy to release BOA-2.1.0 Full Edition, which includes seven new Platforms, many new and important features, many fixes and improvements introduced in the last 6 months since previous Edition.

 
    ### Stable BOA-2.1.0 Release - Full Edition - Now NSA-proof
    ### Date: Sat Nov  2 18:15:19 EDT 2013
    ### Includes Aegir 2.x-boa-custom version.
    
    # Release Notes:
    
      There are some really important changes and improvements in this release
      you should be aware of before running your BOA system upgrade.
    
      Even if you are on a hosted BOA system with upgrades managed for you,
      it is very important to read at least this release notes.
    
      And if you are more curious, read also the giant changelog further below.
    
      Besides all changes, fixes and improvements, all currently supported
      Drupal distributions have been upgraded to use latest Drupal core versions.
    
      Plus, there are seven (7) NEW platforms included!
    
    #-### Control files to customize your BOA system per platform and per site
    
      Almost all control files are now replaced with two centralized,
      platform and site specific INI files, using standard PHP INI format.
    
      The platform specific INI file template with extensive documentation
      included, has filename default.boa_platform_control.ini and is located
      in the sites/all/modules directory.
    
      The site specific INI file template with extensive documentation
      included, has filename default.boa_site_control.ini and is located
      in the sites/foo.com/modules directory.
    
      Any existing control files, both on the platform and site level
      will be automatically converted into active INI files and then deleted
      to avoid confusion, also automatically, on the first run of the special
      maintenance script: /var/xdrago/daily.sh but defaults in the global.inc
      file will allow for smooth, fully automated transition.
    
      This change will improve customizing your BOA system maintainability
      and overall system performance/load thanks to minimized files checks.
    
    #-### Empty and not used platforms auto-cleanup
    
      BOA has finally the ability to auto-delete, during daily maintenance,
      which happens each morning (server time zone), all empty and not used
      platforms. While on all hosted instances the TTL (time-to-live) is set
      to 60 days (counted since last verify task date/time on the platform),
      it can be configured per instance in the /root/.USER.octopus.cnf file
      by changing value of _DEL_OLD_EMPTY_PLATFORMS variable to anything
      higher than 0 (days), which is default (and means the feature is OFF).
    
      Note that every Octopus instance upgrade re-verifies all existing platforms,
      so if you will configure the TTL to 90 days but you will run the upgrade
      every month or every two months, no platforms will ever be deleted.
    
      If you wish to have this TTL customized on the hosted instance, where
      it is set to 60 (days) by default, please open a support ticket via:
      https://omega8.cc/support
    
      Remotely managed BOA systems can have this feature enabled and configured
      upon request submitted via https://omega8.cc/support
    
    #-### All-in-One Site Health Check in your Aegir control panel
    
      You will notice a new Task available on every site page in your Aegir
      Control Panel, named "Run health check". This new task will run a few
      important tests on your site and will store all results in the Task Log,
      so you easily review all results by clicking on the "View" button to the
      right of the task, when it is complete. Make sure to check all details
      by clicking on the "Expand" links in the log.
    
      What are the tests included?
    
      1. The "drush clean-modules" command will be run for you to make sure
         there is no module left in the system table as "enabled" while it
         no longer even exists on the system. This part will utilize (behind
         the scenes) extension: https://drupal.org/project/clean_missing_modules
         If it will find any such leftover, it will clean it up, automatically.
    
      2. The "drush6 pm-updatestatus" command is a native Drush command which
         tells you if there are any waiting module/code updates in the site.
         Note: it will *not* upgrade anything, it is a check only.
         Of course there should be no updates waiting if you follow Aegir
         site upgrade best practices and your site's code is up to date.
         Yes, this check will automatically enable the "update" module for you,
         but it will not auto-disable it afterwards (to not break things in case
         it is required by some other module or feature).
    
      3. The "drush6 status-report" command is a native Drush command
         which provides you a complete overview of your site status.
         Instead of logging into the site, you can review it easily here.
    
      4. The "drush6 updatedb-status" command is a native Drush command
         which tells you if there are any waiting database updates in the site.
         Note: it will *not* apply these updates, it is a check only.
         Of course there should be no updates waiting if you follow Aegir
         site upgrade best practices, but who knows, hence the check.
    
      5. The "drush security-review" command will run only on Drupal 7 based sites
         and provides some additional information by using (behind the scenes)
         this extension: https://drupal.org/project/security_review
    
    #-### PFS (Perfect Forward Secrecy) support in Nginx
    
      BOA now fully supports the most secure, yet still compatible with most
      used systems and browsers SSL configuration.
    
      All hosted BOA instances have been already upgraded automatically and
      you don't need to do anything to make it work -- it is already done
      for you -- both on any SSL enabled site with dedicated certificate
      and IP address and also on the standard, system-wide SSL proxy level,
      which is available for every hosted site -- just type HTTPS:// in the URL.
    
      On self-hosted instances it needs to be enabled by adding a line in your
      /root/.barracuda.cnf file: _NGINX_FORWARD_SECRECY=YES before the upgrade.
      Note that depending on the system used, it may auto-install some
      requirements like latest OpenSSL libraries and packages.
    
      Remotely managed BOA systems can have this feature enabled upon request
      submitted via https://omega8.cc/support
    
    #-### SPDY (new networking protocol) support in Nginx
    
      BOA now fully supports the advanced, new protocol which allows to run
      sites over HTTPS with much better performance than plain HTTP.
    
      While not all browsers support this protocol yet, it is already enabled
      by default on all hosted BOA instances (but obviously works only when you
      access the site via HTTPS:// in the URL).
    
      On self-hosted instances it needs to be enabled by adding a line in your
      /root/.barracuda.cnf file: _NGINX_SPDY=YES before the upgrade.
      Note that depending on the system used, it may auto-install some
      requirements like latest OpenSSL libraries and packages.
    
      Remotely managed BOA systems can have this feature enabled upon request
      submitted via https://omega8.cc/support
    
    #-### Zend OPcache replaced APC in PHP
    
      Newer versions of PHP already come with next generation opcode cache
      from Zend, which is now open-sourced and available also as an extension
      for older PHP versions, including 5.2 and 5.3
    
      BOA leverages this opportunity and now uses Zend OPcache instead of APC.
    
      This change is introduced automatically on all systems, both hosted
      and managed for you and also self-hosted.
    
      Only Debian Squeeze and Ubuntu Precise systems which are using PHP
      installed from packages and not from sources, so with _BUILD_FROM_SRC=NO
      set in the /root/.barracuda.cnf file, still use APC by default.
      You can install Zend OPcache by changing it to _BUILD_FROM_SRC=YES
      before running the upgrade.
    
      Note that Zend OPcache default configuration caches every script for
      60 seconds, so any changes you will introduce, will be visible with
      up to 1 minute delay. However, if there is .dev. or .devel. in the site
      name, this delay is lowered automatically to just 1 second.
    
      You can change the default per site permanently by adding in the
      local.settings.php preferred value, for example, to set it to 10 seconds:
      ini_set('opcache.revalidate_freq', '10'); -- but remember that you will
      override default (1 second) for dev URLs using this method.
    
      Enjoy the most advanced, NSA-proof BOA Edition yet!
    
    # New Octopus platforms:
    
      ### Drupal 7.23.3
    
      Open Academy 1.0-rc3 --------- http://drupal.org/project/openacademy
      Open Atrium 2.0 -------------- http://drupal.org/project/openatrium
      OpenBlog 1.0-a2 -------------- http://drupal.org/project/openblog
      OpenScholar 3.8.1 ------------ http://openscholar.harvard.edu
      Recruiter 1.1 ---------------- http://drupal.org/project/recruiter
      Spark 1.0-a9 ----------------- http://drupal.org/project/spark
      Totem 1.1 -------------------- http://drupal.org/project/totem
    
    # Updated Octopus platforms:
    
      ### Drupal 7.23.3
    
      Commerce 1.20 ---------------- http://drupal.org/project/commerce_kickstart
      Commerce 2.9 ----------------- http://drupal.org/project/commerce_kickstart
      Commons 3.4 ------------------ http://drupal.org/project/commons
      Conference 1.0-a2 ------------ http://drupal.org/project/cod
      Drupal 7.23.3 ---------------- http://drupal.org/drupal-7.23
      Open Deals 1.27 -------------- http://drupal.org/project/opendeals
      Open Outreach 1.2 ------------ http://drupal.org/project/openoutreach
      OpenChurch 1.11-b14 ---------- http://drupal.org/project/openchurch
      Panopoly 1.0-rc5 ------------- http://drupal.org/project/panopoly
      Ubercart 3.5.1 --------------- http://drupal.org/project/ubercart
    
      ### Pressflow 6.28.2
    
      Commons 2.13 ----------------- http://drupal.org/project/commons
      Feature Server 1.2 ----------- http://bit.ly/fserver
      Managing News 1.2.3 ---------- http://drupal.org/project/managingnews
      Open Atrium 1.7.1 ------------ http://drupal.org/project/openatrium
      Pressflow 6.28.2 ------------- http://pressflow.org
      ProsePoint 0.46 -------------- http://prosepoint.org
      Ubercart 2.12.1 -------------- http://drupal.org/project/ubercart
    
    # New features and enhancements in this release:
    
      * Add a workaround for an edge case problem -- a missing /etc/resolv.conf
      * Add auto-config for AdvAgg on both Drupal 7 and Drupal 6.
      * Add command to check for available updates: `drushextra check updates`
      * Add gems for Omega 4 by default.
      * Add sass-globbing gem by default.
      * Allow to install latest OpenSSH from sources with _SSH_FROM_SOURCES
      * Allow to install latest OpenSSL from sources with _SSL_FROM_SOURCES
      * Anonymize lshell intro message.
      * Better code sharing with central core dirs for all built-in platforms.
      * BOA installer wrapper depends on curl instead of wget.
      * Do not stop/start cron if /root/.upstart.cnf control file exists.
      * Drush: Add embedded how-to for aliased commands.
      * Enable views_cache_bully and views_content_cache if views is enabled.
      * Firewall: Disable incoming ping/ICMP.
      * Firewall: Protect port 80 only with CONNLIMIT and remove it from PORTFLOOD.
      * Firewall: Update config template and enable port/syn flood protection
      * FTP: Allow to list/see up to 3000 files/subdirs in a directory.
      * Improve daily.sh performance.
      * Improve dist-upgrade procedure.
      * Improve docs/MODULES.txt
      * Improve meta-installers auto-update procedures.
      * Improve SQL limits auto-configuration.
      * Install pdnsd as a last service.
      * Issue #2000932 - Add also zen-grids.
      * Issue #2015553 - Fix the logic for protected registration of new accounts.
      * Issue #2044589 - SPDY Nginx support.
      * Issue #2052703 - Conversion from control files to ini includes.
      * Issue #2092599 - Switch to disable MySQL password reset on upgrades.
      * Issue #2105477 - Add support for bundler gem.
      * Issue #2116387 - Nginx and PHP: Improve system hardening.
      * Issue #2116395 - Nginx: Better protection and 404 instead of 403.
      * Issue #2118393 - Mark drush/cron as newrelic_background_job
      * Make Bazaar installation optional with BZR keyword required in _XTRAS_LIST
      * Nginx: Use forced HTTPS-only access for Chive and SQL Buddy.
      * PHP: Add experimental support for 5.4 and 5.5
      * PHP: Install Zend OPcache instead of deprecated APC by default.
      * PHP: Reload FPM hourly unless /root/.high_traffic.cnf exists.
      * Restart db server when backup is complete if /root/.my.optimize.cnf exists.
      * Restore support for Expire and Purge modules.
      * Shell: Add gunzip to allowed commands.
      * Shell: Disable mc on the fly unless /root/.allow.mc.cnf control file exists.
      * Shell: Use MySecureShell 1.31 for SFTP by default.
      * Try to download wrapper 4 times before it gives up.
      * Use MySQLTuner to better tune SQL configuration on install and upgrade.
      * Use sqlmagic to fix errors caused by duplicate keys in the db dump.
      * Use standard D7 profile for Ubercart 3 and update related contrib.
      * We no longer depend on drupal.org for any downloads.
      * Add optional, configurable per site, automated and smart (via sqlmagic tool)
        DB table format/engine conversion, enabled per instance with non-default
        _SQL_CONVERT=YES option.
      * Add support for _MODULES_SKIP variable and make the auto-disable agent
        much smarter to never disable any module defined as required by any other
        module or feature.
      * Improve auto-recovery from manual permissions/ownership big mistakes
        related to critical files and dirs.
      * Issue #2067193 - PFS (Perfect Forward Secrecy) support in Nginx with
        _NGINX_FORWARD_SECRECY=YES config option.
      * Use _DEL_OLD_EMPTY_PLATFORMS to enable and define auto-cleanup for old,
        empty platforms with no sites hosted, separately per Satellite instance
        (it does not affect Master instance).
      * Issue #2000932 - Add more Compass tools/extensions: (compass_radix,
        zurb-foundation) and make sure the gems are updated on upgrade.
      * Nginx: Add support for domain specific /robots.txt mapped to static
        files/$host.robots.txt to make it possible to manage it per domain
        also when Domain Access module is used.
      * Improve the logic for daily permissions fix (no longer enabled by default)
        and make it configurable via _PERMISSIONS_FIX variable.
      * Improve the logic for daily modules fix (still enabled by default)
        and make it configurable via _MODULES_FIX variable.
      * Generate static sites/foo.com/files/robots.txt file per site, which is
        mapped to /robots.txt
    
    # New and updated Aegir modules or extensions:
    
      * Add security_review extension
      * Use registry_rebuild 7.x-2.x
    
    # New o_contrib modules:
    
      * Add Advagg 6 and 7 to all platforms.
      * Add force_password_change to all platforms.
      * Add views_cache_bully to all platforms.
    
    # Changes in this release:
    
     * All D6 based sites are forced to use latest PHP 5.3.27 version. 
     * Chive 1.3
      * cURL 7.33.0 as an option.
      * Drush 5.10.0 and 6.1.0 (available as drush5 and drush6)
      * Git 1.8.4.1
      * Lshell 0.9.16.4-om8
      * MariaDB 5.5.33a
      * Nginx 1.5.6
      * Nginx: ngx_cache_purge-2.1
      * OpenSSH 6.3p1 as an option.
      * Percona 5.5.33
      * PHP 5.4.21 and 5.5.5 as an option.
      * Redis 2.6.16
      * Vnstat 1.11
      * Deprecate CiviCRM as a separate platform.
      * Remove obsolete MartPlug distro.
      * Move OpenPublish to unsupported.
      * Move NodeStream to unsupported.
      * Do not include D6 core translations, never included also in D7 platforms.
      * Do not include notoriously buggy backup_migrate module.
    
    # Fixes in this release:
    
      * Add all extra, non-standard options in the barracuda.cnf docs template.
      * Add built-in support for Domain Access also for sites/all/modules/contrib
      * Add exception to support commerce_multicurrency module properly.
      * Add info about self-signed SSL certificate in the welcome e-mail (again).
      * Add support for /usr/etc/sshd_config if exists.
      * Always force update_newrelic - even if there is no new PHP version.
      * Better check for GitHub partial downtime.
      * Better logic for clean resolvconf re-install when needed.
      * Contrib: Make the list readable.
      * Delete too old pid files if any exists.
      * Do not allow to break working DNS cache server with parent system overrides.
      * Do not allow to install OpenSSL and cURL from sources also on Precise.
      * Do not install rsyslog on VZ based VM.
      * Do not set session.cookie_secure on SSL requests for sites 
    <p>
    You can read full changelog as always at: http://bit.ly/newboa</p>
    <p>Enjoy!</p>