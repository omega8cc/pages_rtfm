---
title: BOA-2.3.1 Full Edition
slug: boa-231-full-edition-333
menu: BOA-2.3.1 Full Edition
date: 14-09-2014
published: true
publish_date: 14-09-2014
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.3.1 Full Edition, which includes latest Aegir 2.1 enhanced version with new features, including sites in subdirectories, self-managed Solr 4 cores, easy to use New Relic integration, plus many changes, improvements and bug fixes.

 
    ### Stable BOA-2.3.1 Release - Full Edition
    ### Date: Sun Sep 14 15:53:25 SGT 2014
    ### Includes Aegir 2.1 with improvements
    ### Latest hotfix added on: Mon Sep 15 19:10:07 SGT 2014
    
    # Release Notes:
    
      This major BOA Edition introduces many new features, changes and fixes.
    
      You should carefully read about some caveats further below **before** running
      this major upgrade on your system. Please secure a fresh system backup first.
    
      If you haven't run full barracuda+octopus upgrade to latest BOA Stable
      Edition yet, don't use any partial/system upgrade modes.
    
      Once new BOA Stable is released, you must run *full* upgrades with commands:
    
      $ cd;wget -q -U iCab http://files.aegir.cc/BOA.sh.txt;bash BOA.sh.txt
      $ barracuda up-stable
      $ octopus up-stable all both
    
      @=> Key new features:
    
      * BOA-2.3.1 comes with new, shiny Aegir 2.1 stable version!
      * Support for Drupal sites in subdirectories is enabled by default
      * Solr 4 cores can be added/updated/deleted via site level INI settings
      * Super-easy to use New Relic support with per Octopus license key
      * Ability to add new Octopus instances with new, simple command syntax
    
      @=> Aegir control panel new features:
    
      * The list of sites is searchable by name or installation profile
      * Sites have dedicated tabs: Backups, Task log, Edit and Packages
      * Platform have tabs: Add site, Clients, Task log, Edit and Packages
      * You can schedule tasks against filtered sites in batches
      * Scheduling tasks in batches is available also on the platform view
      * Scheduling tasks in batches is available also on the profile view
      * Scheduling tasks in batches is available also on the client view
      * You can schedule tasks also against platforms in batches
      * You can safely apply db updates via 'Run db updates' task on any site
      * The new 'Clients' menu item allows to list and manage sub-accounts
      * Profiles are listed with both human-readable and machine names
      * It is now possible to choose any existing alias or the main site name
        as a redirect target, but without the need to rename the site --
        it will just re-verify the site and create new vhost automatically
    
      @=> Aegir control panel changes:
    
      * The hosting/signup form is still available but not included in the menu
      * The node/add/site form is no longer included in the main menu
      * The optional pseudo-CDN-aliases feature is now disabled by default
    
      @=> Other important changes:
    
      * Support for PHP 5.2 has been officially deprecated
      * The www53 PHP-FPM pool has been switched from port to default socket mode
      * All existing vhosts must use wildcard in the Nginx 'listen' directive
      * Legacy mode for Install and Upgrade moves to 2.2.x branch
      * DB credentials are no longer in settings.php, only in drushrc.php
      * Latest Drush 6 version is used in the Aegir backend by default
    
      But what if you are not ready for this major upgrade and you would like
      to have more time for testing, but still be able to run system upgrades,
      thus effectively still using previous version 2.2.9 ?
    
    #-### Legacy mode for Install and Upgrade moves to 2.2.x branch
    
      From now on, the 'legacy' install and upgrade mode available in all meta-
      installers will utilize branch 2.2.x instead of deprecated 2.1.x series.
    
      This means that starting with meta installers updated to use BOA-2.3.1
      version you can use commands like shown below to update Barracuda, Octopus
      and also to install more Octopus instances, while still using version 2.2.9:
    
      $ boa in-legacy public server.mydomain.org my@email o1
      $ barracuda up-legacy system
      $ octopus up-legacy o1
      $ boa in-legacy public server.mydomain.org my@email o2 mini
      etc.
    
      Remember to update your meta-installers first!
    
      $ cd;wget -q -U iCab http://files.aegir.cc/BOA.sh.txt;bash BOA.sh.txt
    
      Note also that if you will upgrade to current 'stable', it is not possible
      to downgrade back to the 'old stable' with 'legacy' mode, so please proceed
      with care!
    
      Remember also that current legacy version will not receive any further
      updates, even for security issues (besides those provided as packages by
      your OS vendor - Debian or Ubuntu, which will still work), because it is
      already different enough from current 2.3.1 stable, so we can't reliably
      maintain both with working upgrade path.
    
    #-### Caveats: This upgrade will force wildcard in the Nginx 'listen' directive
    
      If you have old enough BOA system which still uses legacy IP mode and not
      a wildcard in the Nginx 'listen' directive, which is both Aegir and BOA
      standard for a long time already, this upgrade will fix the problem and
      update directives only in vhosts known and controlled by BOA.
    
      If you have any other vhosts, located in standard or non-standard Nginx/BOA
      directories for vhosts, you have to update them manually after upgrade to
      BOA-2.3.0 or newer, or they will take over all other vhosts on the system
      and cause redirects to /install.php which results with Nginx error 403 or 404,
      depending on the prior configuration.
    
      It will happen because IP based 'listen' directive in Nginx has higher
      priority, and will mess things horribly if there are vhosts using wildcard
      and some using the main system IP address.
    
      What and how to replace? Here are the commands you need to run as root:
    
        $ sed -i "s/.*listen.*:80;/  listen  \*:80;/g" /path/to/vhost.file
        $ service nginx reload
    
      Note: this **doesn't** affect special vhosts for SSL enabled sites, if used,
      because they are designed to use IP based 'listen' directives to provide
      separation between SSL enabled IPs and their associated certificates,
      while their associated 'upstream' block may even point to either local or
      remote IP address, so there is no wildcard to use in this case, and it will
      not conflict with all other vhosts managed by Aegir, because all SSL enabled
      vhosts listen on other IP addresses than the main system IP, which is
      by default used by all vhosts with wildcard in the 'listen' directive.
    
      The problem may happen only when you have vhosts using wildcard and also
      some vhosts using **main** system IP address in the 'listen' directive,
      which may happen also unintentionally during upgrade to BOA-2.3.0 or never,
      if there are either vhosts BOA doesn't control, or there are ghost vhosts
      not yet purged if you didn't upgrade to BOA-2.2.9 before, or there are
      some disabled sites, so their vhosts will not be re-created by Aegir
      during this major upgrade (because only active sites can be re-verified).
    
      While BOA will fix also any such ghost vhosts anyway, it will not be able
      to detect and fix vhosts outside of the standard directories managed by Aegir.
    
    #-### Ability to add new Octopus instances with new, simple command syntax
    
      It is now possible to add stable Octopus instances w/o forcing Barracuda
      upgrade, plus optionally with no platforms added by default -- usage:
    
        $ boa {in-octopus} {email} {o2} {mini|max|none}
    
    #-### The www53 PHP-FPM pool has been switched from port to default socket mode.
    
      Note that we are breaking backward compatibility here, so it will cause
      downtime on upgrade from any too old BOA version, until you will upgrade also
      Octopus instance(s) and update any other non-standard vhosts or includes
      still using legacy port mode for 'fastcgi_pass' Nginx directive.
    
      If you have 'fastcgi_pass 127.0.0.1:9090;' in any custom vhost or Nginx
      include file on the Octopus instance, you should replace it with:
    
        fastcgi_pass unix:/var/run/o1.fpm.socket;
    
      where 'o1' is your corresponding Octopus system username.
    
      Note that if you have custom vhosts or includes in the Aegir Master Instance,
      you should instead replace 'fastcgi_pass 127.0.0.1:9090;' with:
    
        fastcgi_pass unix:/var/run/www53.fpm.socket;
    
      where '53' is related to PHP version defined via _PHP_FPM_VERSION in your
      /root/.barracuda.cnf file. Note that while variable has a dot, the socket
      name doesn't.
    
    #-### Support for PHP 5.2 has been officially deprecated
    
      While Barracuda 2.3.1 can continue to run and even upgrade if needed also
      the very old PHP 5.2 version, only Octopus instances running at least PHP 5.3
      or newer in both FPM and CLI mode can be upgraded to Octopus 2.3.1 Edition.
    
      If you are still using PHP 5.2 in your Octopus instance, you will not
      receive Aegir nor Drupal Platforms upgrade, but the Barracuda part of your
      system will receive upgrade to 2.3.1 anyway, so it will be ready to support
      your outdated Octopus instance upgrade as soon as you will switch it to
      modern and secure PHP version -- which is easy!
    
      Let's quote the original how-to for reference:
    
    #-### Support for PHP FPM/CLI version safe switch per Octopus instance
    
      This allows to easily switch PHP version by the instance owner w/o system
      admin (root) help. All you need to do is to create ~/static/control/fpm.info
      and ~/static/control/cli.info file with a single line telling the system
      which available PHP version should be used (if installed): 5.5 or 5.4 or 5.3
    
      Only one of them can be set, but you can use separate versions for web access
      (fpm.info) and the Aegir backend (cli.info). The system will switch versions
      defined via these control files in 5 minutes or less. We use external control
      files and not any option in the Aegir interface to make sure you will never
      lock yourself by switching to version which may cause unexpected problems.
    
    #-### Support for New Relic monitoring with per Octopus instance license key
    
      This new feature will disable global New Relic monitoring by deactivating
      server-level license key, so it can safely auto-enable or auto-disable it
      every 5 minutes, but per Octopus instance -- for all sites hosted on
      the given instance -- when a valid license key is present in the special
      new ~/static/control/newrelic.info control file.
    
      Please note that valid license key is a 40-character hexadecimal string
      that New Relic provides when you sign up for an account.
    
      To disable New Relic monitoring for the Octopus instance, simply delete
      its ~/static/control/newrelic.info control file and wait a few minutes.
    
      Please note that on a self-hosted BOA you still need to add your valid
      license key as _NEWRELIC_KEY in the /root/.barracuda.cnf file and run
      system upgrade with at least 'barracuda up-stable' first. This step is
      not required on Omega8.cc hosted service, where New Relic agent is already
      pre-installed for you.
    
    #-### Solr 4 cores can be added/updated/deleted via site level INI settings
    
    ;;
    ;;  This option allows to activate Solr 4 core configuration for the site.
    ;;
    ;;  Only Solr 4 powered by Jetty server is available. Supported integration
    ;;  modules are limited to latest versions of either search_api_solr (D7 only)
    ;;  or apachesolr (will use Drupal core specific version automatically).
    ;;
    ;;  Currently used versions are listed below:
    ;;
    ;;    http://ftp.drupal.org/files/projects/search_api_solr-7.x-1.6.tar.gz
    ;;    http://ftp.drupal.org/files/projects/apachesolr-7.x-1.7.tar.gz
    ;;    http://ftp.drupal.org/files/projects/apachesolr-6.x-3.0-rc2.tar.gz
    ;;
    ;;  Note that you still need to add preferred integration module along with
    ;;  any its dependencies in your codebase since this feature doesn't modify
    ;;  your platform or site - it only creates Solr core with configuration
    ;;  files provided by integration module: schema.xml and solrconfig.xml
    ;;
    ;;  This setting affects only the running daily maintenance system behaviour,
    ;;  so you need to wait until next morning to be able to use new Solr 4 core.
    ;;
    ;;  Once the Solr core is ready to use, you will find a special file in your
    ;;  site directory: sites/foo.com/solr.php with details on how to access
    ;;  your new Solr core with correct credentials.
    ;;
    ;;  The site with enabled Solr core can be safely migrated between platforms,
    ;;  integration module can be moved within your codebase and even upgraded,
    ;;  as long as it is using compatible schema.xml and solrconfig.xml files.
    ;;
    ;;  Supported values for the solr_integration_module variable:
    ;;
    ;;    apachesolr
    ;;    search_api_solr
    ;;
    ;;  To delete existing Solr core simply comment out this line.
    ;;  The system will cleanly delete existing Solr core next morning.
    ;;
    ;solr_integration_module = NO
    
    ;;
    ;;  This option allows to auto-update your Solr 4 core configuration files:
    ;;
    ;;    schema.xml
    ;;    solrconfig.xml
    ;;
    ;;  If there is new release for either apachesolr or search_api_solr, your
    ;;  Solr core will not be automatically upgraded to use newer schema.xml and
    ;;  solrconfig.xml, unless allowed by switching solr_update_config to YES.
    ;;
    ;;  This option will be ignored if you will set solr_custom_config to YES.
    ;;
    ;solr_update_config = NO
    
    ;;
    ;;  This option allows to protect custom Solr 4 core configuration files:
    ;;
    ;;    schema.xml
    ;;    solrconfig.xml
    ;;
    ;;  To use customized version of either schema.xml or solrconfig.xml, you need
    ;;  to switch solr_custom_config to YES below and if you are using hosted
    ;;  Aegir service, submit a support ticket to get these files updated with
    ;;  your custom versions. On self-hosted BOA simply update these files directly.
    ;;
    ;;  Please remember to use Solr 4 compatible config files.
    ;;
    ;solr_custom_config = NO
    
    
    # Updated Octopus platforms:
    
      aGov 1.4 --------------------- https://drupal.org/project/agov
      Guardr 1.12 ------------------ https://drupal.org/project/guardr
      Open Academy 1.1 ------------- https://drupal.org/project/openacademy
      Restaurant 1.0-b9 ------------ https://drupal.org/project/restaurant
      Ubercart 3.7 ----------------- https://drupal.org/project/ubercart
    
    # New features and enhancements in this release:
    
      * Ability to add new Octopus instances with new, simple command syntax
      * Add default aggressive php-fpm monitoring + /root/.no.fpm.cpu.limit.cnf
      * Allow to define always disabled modules via _MODULES_FORCE variable.
      * Better wait limits on connection testing for slow network / long distance.
      * Issue #1927522 - Add support for easy Solr cores self-management.
      * Issue #362 - Add imageapi_optimize binaries via IMG in _XTRAS_LIST
      * Issue #376 - Add New Relic support with per Octopus instance license key.
      * Make firewall management faster with randomized schedule.
      * Procs monitor runs every 3 seconds.
      * Run mysql_proc_control every 5 seconds for better results.
      * You can safely apply db updates via 'Run db updates' task on any site.
    
    # Changes in this release:
    
      * DB credentials are no longer visible in settings.php, only in drushrc.php
      * Delete default profiles in the hostmaster platform.
      * Disable _DEBUG_MODE if not enabled on the fly.
      * Disable newrelic-sysmond unless /root/.enable.newrelic.sysmond.cnf exists.
      * Drush: Upgrade command line version 6 to mini-6-14-09-2014
      * Nginx: Remove deprecated code - _HTTP_WILDCARD is already used by default.
      * Nginx: Use limit_conn protection only for known dynamic requests.
      * Redis Integration Module (cache_backport): Update to version 6.x-1.0-rc2
      * Redis Integration Module: Update to version mod-12-09-2014
      * Remove _ALLOW_UNSUPPORTED legacy and no longer working properly feature.
      * Remove dependency on Update Manager globally.
      * Remove deprecated multi-instance labels in the New Relic configuration.
      * Replace old hosting_civicrm_cron with newer hosting_civicrm module.
      * Set hosting_default_profile to 'minimal' to improve Ubercart 3 visibility.
      * The www53 PHP-FPM pool has been switched from port to default socket mode.
      * Use Provision CiviCRM boa-2.3.1-dev
    
    # System upgrades in this release:
    
      * cURL 7.38.0 (if installed from sources)
      * Git 2.1.0 (if installed from sources)
      * Jetty 7.6.16.v20140903
      * Jetty 8.1.16.v20140903
      * Jetty 9.2.3.v20140905
      * PHP 5.3.29 EOL! Please read: http://php.net/archive/2014.php#id2014-08-14-1
      * PHP 5.4.32
      * PHP 5.5.16
      * Redis 2.8.14
    
    # Fixes in this release:
    
      * Add cleanup for _GIT_FORCE_REINSTALL if added in .barracuda.cnf
      * Add missing drush cache-clear drush to improve upgrade path.
      * Add new features in the README.txt
      * Add wheezy to the exceptions list where required.
      * Allow to clear drush cache without directory restrictions.
      * Always set correct TMP path for supported users.
      * Cleanup for cron pid files in user specific .tmp dirs.
      * Count properly also symlinked files directories (improved).
      * D6 colorbox module requires old 1.3.18 library.
      * Delete drush_make leftovers.
      * Delete duplicate menu items on upgrade.
      * Do not allow to install SSH from sources on Trusty to avoid problems.
      * Do not skip daily.sh during barracuda system only update.
      * Eldir theme: Use max width for buttons, if possible.
      * Explain why installing RVM may take longer than expected.
      * Fix cleanup for drush aliases in sub-accounts.
      * Fix daily cleanup for user specific .tmp directories.
      * Fix docs/HINTS.txt
      * Fix for broken mariadb.list
      * Fix for broken, way too aggressive PHP-FPM monitoring.
      * Fix for ghost dirs cleanup.
      * Fix for ghost vhosts cleanup.
      * Fix for missing symlinks to existing platforms.
      * Fix for not working protection from blocking local IPs on multi-IP systems.
      * Fix for subdirs_support universal check.
      * Fix for unreliable _IS_OLD check on Octopus instances upgrade.
      * Fix for warning "Could not create directory ." on Hostmaster site Verify.
      * Fix the fields order in the site edit form.
      * Fix the regex to not whitelist unexpected IP ranges inadvertently.
      * Force cURL rebuild if installed with outdated OpenSSL version.
      * Guard against destructive or insecure tasks run on the hostmaster site.
      * Improve cleanup for empty platforms directories.
      * Improve monitoring to protect against convert trying to overload the system.
      * Issue #2330781 - Use Drush dt() wrapper instead of not always available t()
      * Issue #357 - Fix the logic for Git (re)install from sources.
      * Issue #360 - Exclude special --CDN vhosts from daily cleanup.
      * Issue #361 - Update and improve docs/FAQ.txt
      * Issue #369 - Automatically download and fix /bin/websh if missing.
      * Issue #369 - Restore classic /bin/sh symlink automatically if needed.
      * Issue #373 - Set correct TMP, TEMP, TMPDIR env variables in limited shell.
      * Issue #373 - Too restrictive lshell forbidden list breaks drush sql-sync.
      * Issue #380 - Nameserver / pdnsd problem -- Fixes also Issue #2007990.
      * Issue #381 - Zend OPcache forced adds useless noise in the log.
      * Issue #388 - Version 6.x-2.x of provision_civicrm requires hosting_civicrm
      * Issue #389 - hosting_civicrm breaks site install form with confusing error.
      * Issue #390 - Duplicate platforms nodes are created after upgrade to 2.3.0
      * Issue #395 - Validate username isn't reserved before running install script.
      * Issue #396 - Locale isn't getting set properly.
      * Issue #397 - Not actually prompted for platforms during installation.
      * Issue #398 - Make locales setup/fix for Debian always OS compatible.
      * Issue #399 - The hitimes gem needs to be pre-installed to support Omega4.
      * Issue #400 - CiviCRM is not installed on 2.3.0
      * Issue #401 - Create sites/all/* subdirs in Hostmaster early enough.
      * Issue #402 - Fix for ghost or disabled vhosts which still listen on IP.
      * Issue #405 - Installer hangs due to yes/no dialog - "Untrusted packages"
      * Issue #406 - Force keyring reinstall also upon 'GPG error'.
      * Issue #407 - Fix for 'username is already taken' error on a local VM install
      * Issue #408 - Fix for multiple funny typos. Thanks ar-jan!
      * Make it clear that subdomain and subdirectory name must be identical.
      * Make sure that keys subdirectory exists to avoid active platforms cleanup.
      * Make the PHP-FPM processes monitor less aggressive by default.
      * New Relic not enabled if no custom ~/static/control/{fpm|cli}.info exists.
      * Nginx: Add config symlinks only on legacy instances.
      * Nginx: Add cron access support for subdir sites.
      * Nginx: Convert all vhosts to wildcard mode on Barracuda upgrade.
      * Nginx: Disable monitoring for POST requests related to cart/checkout URI.
      * Nginx: Do not touch nginx_wild_ssl.conf during this upgrade.
      * Nginx: Improve wildcard conversion procedure on some really old instances.
      * Nginx: Remove deprecated code and config templates.
      * Nginx: Sanitize aliases in vhost_disabled.tpl.php to avoid warnings.
      * Nginx: Update config includes to match optional BOA features improvements.
      * Nginx: Update unified configuration templates in Provision to unfork BOA.
      * Nginx: Update vhosts templates to match BOA improvements.
      * PHP: Avoid unintended duplicate rebuilds.
      * PHP: Sync disable_functions list.
      * Protect sites/all/drush
      * Provision: Backport provision_hosting_feature_enabled()
      * Provision: Remove legacy subdir code and update checks.
      * Redis config should sync with PHP-CLI, not PHP-FPM.
      * Remove legacy procs monitoring code.
      * Remove no longer needed limreq global fixes.
      * Remove no longer needed/used contrib updates.
      * Remove redundant file_exists() if is_readable() is also used.
      * Replace old hosting_civicrm_cron with newer hosting_civicrm module.
      * Restart pdnsd before running barracuda upgrade.
      * Restore BOA formatting for tasks log to improve readability.
      * Restore BOA naming convention and docs in Hostmaster.
      * Restore BOA naming convention for Installation profiles in Hostmaster.
      * Restore BOA strict _hosting_valid_fqdn* testing procedures in Hostmaster.
      * Restore BOA weight defaults in the form in Hostmaster.
      * Restore punycode in Hostmaster.
      * Restore tasks sort to always show tasks scheduled and running at the top.
      * Sanitize cli.info and fpm.info
      * Set _PLATFORMS_LIST properly.
      * Silence early sed replacements to avoid confusion.
      * Simplify colorbox-1.3.18 download.
      * Simplify colorbox-1.5.13 download.
      * Switch branch on the fly and add support for Aegir vanilla mode.
      * Sync /tmp access restrictions.
      * The hosting_civicrm_cron is now a submodule and should be also auto-enabled.
      * The wildcard transition **doesn't** affect vhosts for SSL enabled sites.
      * There is no need to force backend clone from GitHub on initial upgrade.
      * Update for the Hostmaster welcome page.
      * Update FPM monitoring settings.
      * Use as short labels on the site node as possible.
      * Use control files properly to not run redundant Jetty/Solr upgrade.
      * Use correct paths to platform level drushrc.php file.
      * Use correct Provision version on initial upgrade to 2.3.0
      * Use Drush6 with @hostmaster.
      * Use is_dir() instead of file_exists() when checking directory existence.
      * Use is_file() and is_link() instead of file_exists() before trying unlink()
      * Use is_readable() and file_exists() instead of file_exists() for backup.
      * Use is_readable() check instead of insufficient file_exists() for includes.
      * Use is_readable() instead of file_exists() when checking alias existence.
      * Install latest Git even if not specified via _XTRAS_LIST but previous
        version built from sources is detected.
      * Issue #2278847 - Derivatives can't be created on install with Drush and
        Aegir or when no vhost is available yet (Drupal Commons)


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!