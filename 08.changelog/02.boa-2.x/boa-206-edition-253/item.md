---
title: BOA-2.0.6 Edition
slug: boa-206-edition-253
menu: BOA-2.0.6 Edition
date: 01-04-2013
published: true
publish_date: 01-04-2013
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.0.6 Edition, which includes 1 new and 18 updated platforms, new Drupal 7 and Drupal 6 core versions and many changes, fixes and improvements introduced in the last three months since previous Edition.

 
    ### Stable Edition BOA-2.0.6
    ### Date: Mon Apr  1 21:34:04 EDT 2013
    ### Installs Aegir 2.x
    
    # New Octopus platforms:
    
      ### Drupal 7
    
      Commons 3.1 ------------------ http://drupal.org/project/commons
    
    # Updated Octopus platforms:
    
      ### Drupal 7
    
      CiviCRM 4.2.8 ---------------- http://civicrm.org
      Commerce 1.16 ---------------- http://drupal.org/project/commerce_kickstart
      Commerce 2.5 ----------------- http://drupal.org/project/commerce_kickstart
      Drupal 7.21.2 ---------------- http://drupal.org/drupal-7.21
      NodeStream 2.0-rc4 ----------- http://drupal.org/project/nodestream
      Open Deals 1.18 -------------- http://drupal.org/project/opendeals
      Open Outreach 1.0-rc10 ------- http://drupal.org/project/openoutreach
      OpenChurch 1.11-beta9 -------- http://drupal.org/project/openchurch
      Panopoly 1.0-rc4a ------------ http://drupal.org/project/panopoly
      Ubercart 3.4.1 --------------- http://drupal.org/project/ubercart
    
      ### Pressflow 6
    
      Acquia 6.28.1 ---------------- http://bit.ly/acquiadrupal
      Commons 2.12 ----------------- http://drupal.org/project/commons
      Feature Server 1.2 ----------- http://bit.ly/fserver
      Managing News 1.2.3 ---------- http://drupal.org/project/managingnews
      Open Atrium 1.7.1 ------------ http://drupal.org/project/openatrium
      Pressflow 6.28.1 ------------- http://pressflow.org
      ProsePoint 0.46 -------------- http://prosepoint.org
      Ubercart 2.11.1 -------------- http://drupal.org/project/ubercart
    
      All other not listed above platforms are available with latest
      D6 or D7 core, even if there were no new distro version released.
    
    # No longer supported Octopus platforms:
    
      The platforms listed below can be re-added when their maintainers
      will fix all critical issues and/or apply required updates:
    
      ELMS ------------------------- http://drupal.org/project/elms
      MartPlug --------------------- http://drupal.org/project/martplug
      Octopus Video ---------------- http://octopusvideo.org
      Open Academy ----------------- http://drupal.org/project/openacademy
      Open Enterprise -------------- http://drupal.org/project/openenterprise
      OpenPublic ------------------- http://drupal.org/project/openpublic
      OpenScholar ------------------ http://openscholar.harvard.edu
      Videola ---------------------- http://videola.tv
    
    # New features:
    
      * Add an option to allow cron based, unattended system-only upgrades.
      * Add randpass helper script.
      * Add support for wkhtmltoimage.
      * Add syncpass tool to repair broken instances after incomplete upgrade.
      * Allow to specify extra apt-get packages with _EXTRA_PACKAGES option.
      * Allow to tune PHP-CLI timeout in the BOND script with separate option.
      * Install auditd with aureport by default.
      * Issue #1479300 - Add optional LDAP support in Nginx.
      * Issue #1876418 - Support for High-performance JavaScript callback handler.
      * Issue #1916804 - Validated bypass of flood control based on tty.
      * Jetty: Make migration from Tomcat easy with _TOMCAT_TO_JETTY=YES
      * PHP: Allow to use _PHP_EXTRA_CONF for custom builds from src.
      * Redis: Add Lock Backend Support for Drupal 6 and Drupal 7.
      * Redis: Enable lock support if modules/redis_lock_enable.info exists.
      * Shell: Add extra Drush versions available as drush4, drush5 and drush6.
      * SOLR: Support for 1.x / Jetty 7, 3.x / Jetty 8 and 4.x / Jetty 9.
      * SOLR: Use Jetty 8 for Solr 4 on systems with Java 1.6 available.
      * SOLR: Use Jetty 9 for Solr 4 on systems with Java 1.7 available.
      * SQL: Add sqlmagic tool to fix SQL dumps and convert to/from InnoDB/MyISAM.
      * SQL: Make default_storage_engine configurable with _DB_ENGINE option.
      * Use Registry Rebuild with Fixed Redis Lock Support aware configuration.
      * Allow to force SERVER_NAME based $cookie_domain with special
        modules/cookie_domain.info control file per site.
    
    # New Aegir modules or extensions:
    
      * Add drush clean-modules command - clean_missing_modules extension.
      * Add drush_ecl extension - Drush Entity Cache Loader.
      * Add hosting_site_backup and provision_site_backup enabled by default.
    
    # Changes:
    
      * Git 1.8.2
      * MariaDB 5.5.30
      * Nginx 1.3.15
      * Percona 5.5.30
      * PHP 5.3.23
      * Redis 2.6.12
      * Deprecate CiviCRM 3.4.8 D6 - only available with _ALLOW_UNSUPPORTED=YES.
      * Do not force filefield_nginx_progress as enabled also for D7.
      * Drupal 8.0-dev-tested deprecated and moved to unsupported group.
      * ELMS 1.0-beta1 deprecated and moved to unsupported group.
      * Enable entitycache module by default.
      * Master Aegir: Re-create secure db password on every barracuda upgrade.
      * Master Aegir: Sync generating secure db password also on barracuda install.
      * Nginx: Set 24h Speed Booster cache TTL for spiders/bots by default.
      * NodeStream 1.5.1 deprecated and moved to unsupported group.
      * Open default MongoDB port 27017 for outgoing connections.
      * OpenScholar deprecated and moved to unsupported group.
      * PHP: Deprecate 5.2 also on upgrade.
      * PHP: Install MongoDB driver if MNG keyword is listed in _XTRAS_LIST.
      * PHP: Set _PHP_CLI_VERSION=5.3 by default.
      * PHP: Switch to forced CLI 5.3 and FPM 5.3 also in the custom config.
      * PHP: Switch to FPM 5.3 also for D6 sites by default.
      * Pressflow 5.23 deprecated and moved to unsupported group.
      * Redis: Re-create secure password on every barracuda upgrade.
      * Satellite Aegir: Re-create secure db password on every octopus upgrade.
      * SQL: Do not run DB OPTIMIZE unless /root/.my.optimize.cnf ctrl file exists.
      * SQL: Re-generate new secure mysql root password on every barracuda upgrade.
      * SQL: Use key_buffer = 2M by default.
      * SQL: Use more safe memory limits after introducing higher key_buffer_size
      * Use better names for various control files.
      * Watch crons running > 2 min and kill crons running > 3 min.
      * Split _XTRAS_LIST into two groups: included via ALL keyword and
        other which need to be listed explicitly.
    
    # Fixes:
    
      * Add Ksplice-aware kernel upgrade alert.
      * Add some delay to avoid race conditions when removing more zombies.
      * Allow higher system load before disabling access for spiders temporarily.
      * Always send upgrade log when running in the silent mode.
      * Avoid cron collisions and make sure all maintenance tasks run 0-6 AM.
      * Better and separate backup rotation on hostmaster upgrade.
      * Better check if Webmin GnuPG signing key has been added properly.
      * Better fix for $cookie_domain and DA compatibility.
      * Better protection for all ports usually targeted in brute force attacks.
      * Check if nproc is present and fall back to /proc/cpuinfo otherwise.
      * Clean swap on kernel tuning update.
      * Delete broken o_contrib symlinks before trying to recreate them.
      * Do not add and remove bind from /etc/sudoers since it is not supported.
      * Do not block @ in the limited shell - it breaks git foo git@bar etc.
      * Do not force _DEBUG_MODE=YES if not required.
      * Do not force _HTTP_WILDCARD=NO for stock install option.
      * Do not run extra IP checks for requests below $mininumber threshold.
      * Do not run initial apticron check in local install.
      * Do not run two mysql restarts in a row on mysql upgrade.
      * Downgrade to working wkhtmltopdf-0.10.0_rc2 and wkhtmltoimage-0.10.0_rc2
      * Drupal 7.x core with Field API memory optimization - see #1915646
      * Enable image_allow_insecure_derivatives to avoid issues with drupal-7.20
      * Fix apticron to suggest barracuda up-stable instead of apt-get upgrades.
      * Fix AWS system auto-discovery and auto-configuration.
      * Fix Drush 5.x and _USE_STOCK support.
      * Fix for Bazaar (bzr) 2.6b2 extensions build.
      * Fix for pdnsd install on Ubuntu Precise.
      * Fix the 32 long ALNUM password generation for lshell users.
      * Fix the hint to just display the uptrack command, not run it.
      * Force logrotate on demand if /var/log/syslog > 1GB
      * Force mysql tables check and upgrade before hostmaster upgrade.
      * Force proper pdnsd and resolvconf re-installation if needed.
      * Force proper resolvconf configuration to support and use pdnsd server.
      * FTPS on all modern systems requires lshell path added in /etc/shells.
      * Hostmaster/Octopus contrib modules are now added via Aegir makefile.
      * Improve autonomous IDS auto-cleaning and permanent block mgmt.
      * Improve compatibility testing with Drush 5 and Drush 6.
      * Improve kernel default tuning.
      * Improve Master Instance upgrade logic.
      * Improve mysqldump performance by default.
      * Improve the default strict configuration for $cookie_domain.
      * Improve Tomcat/Jetty self-healing to avoid stuck processes.
      * Install also hostmaster contrib when stock option is used.
      * Issue #1782034 - Use fixed version of the message_notify module.
      * Issue #1825018 - Disable binary logging and make it optional.
      * Issue #1871060 - CiviCRM 4.2.6 needs separate civicrml10n fix.
      * Issue #1873478 - Localhost install broken because getent test is used.
      * Issue #1875348 - Fix for Nginx 1.3.10 bug causing random segfaults.
      * Issue #1886920 - Fix the unrecognized option [service=system-auth] error.
      * Issue #1886920 - Pure-FTPd config broken because of deprecated pam_stack.so
      * Issue #1888380 - Deleted platform cache folder recreated automatically.
      * Issue #1889322 - Domain Access module breaks sites provisioning.
      * Issue #1897018 - Set Pin-Priority also in wrappers to fix also stable.
      * Issue #1897018 - Ubuntu Precise breaks install and upgrade.
      * Issue #1906760 - Incomplete access_log directive in the purge vhost.
      * Issue #1906900 - Nginx microcaching not disabled on prefixed admin URIs.
      * Issue #1909208 - Changed MariaDB GnuPG signing key hangs install/upgrade.
      * Issue #1913394 - Disable automatic CSF/LFD upgrade.
      * Issue #1913488 - Do not install GEOS PHP ext. unless explicitly listed.
      * Issue #1914294 - APC 3.1.14 disappeared from PECL - downgrade to 3.1.13
      * Issue #1918722 - Add diff command as allowed in the limited shell.
      * Issue #1920972 - Could not change permissions warnings on site verify.
      * Issue #1932388 - Use correct keyword PPY for Panopoly install.
      * Issue #1935388 - Use reliable check for Master Instance install path.
      * Issue #1947082 - Permissions are never fixed on the profile level.
      * Issue #1949740 - Make sure that cache_prefix for Redis is always set.
      * Issue #1952042 - Make strong passwords optional and not default.
      * Issue #1953248 - Extra Drush versions should be added properly.
      * Issue #1957762 - Upgrade to Bazaar (bzr) 2.6b2
      * Jetty: Tune memory limits automatically to avoid extra RAM requirements.
      * Keep all extra modules in the same profiles/hostmaster/modules directory.
      * Lshell: Allow ping command to help keep session active / auto-whitelist.
      * Make apticron aware of the BOA version currently running.
      * Make BOND aware of _CUSTOM_CONFIG_SQL if present.
      * Make Compass Tools available in the standard path, if installed.
      * Make sure that all removed zombies use unique dir names.
      * Make sure that all users home dirs are protected.
      * Make sure that now redundant hosting_backup_gc module is removed.
      * Make sure that SERVER_NAME is set to HTTP_HOST early enough, if required.
      * Make the errors monitor aware of system only upgrade mode.
      * Make URI filtering regex localization-aware in the global.inc
      * Nginx Security: BEAST attack protection and fix for PCI compliance.
      * Nginx: Another fix for broken imagecache paths in some imported sites.
      * Nginx: Better protection from DoS attempts on never cached uri.
      * Nginx: Do not block spiders on imagecache/styles URIs.
      * Nginx: Do not force use epoll - it is set on install properly.
      * Nginx: Do not force worker_connections. It will not work in the VM guest.
      * Nginx: Do not force worker_rlimit_nofile. It will not work in the VM guest.
      * Nginx: Force rebuild to include LDAP support if enabled via _NGINX_LDAP=YES
      * Nginx: Improve Abuse Guard to better protect from imagecache|styles flood.
      * Nginx: Improve no-cache exceptions for known AJAX and webform requests.
      * Nginx: Make json compatible with boost caching but dynamic for POST.
      * Nginx: Restore fast 404 for static json requests.
      * Nginx: Set workers number to available CPUs x2 with min/max defaults.
      * Nginx: Use default buffer=32k in the access_log for better performance.
      * Nginx: Use static /normal/ instead of dynamic /$device/ for Boost cache.
      * PHP: Enable more FPM workers by default for better performance.
      * PHP: Force php53-fpm restart if there is no master process running.
      * PHP: Many Drupal 7 based distros require 196M limit at minimum.
      * PHP: Never force php53-fpm restart when another script reloads it.
      * PHP: Use more safe limits on low memory systems.
      * Prevent turning the feature server site into a spam machine.
      * Protect also from not supported request types if Nginx server is busy.
      * Randomize tasks wait/start intervals better to avoid high system load.
      * Redis: Do not disable it on the fly when there is /nojs/ in the URI.
      * Redis: Double check if $cache_lock_path exists before using it.
      * Redis: No need to force exception for cache_menu bin.
      * Redis: Tune sysctl for better memory management by default.
      * Remove up to two last zombies on Master Instance upgrade.
      * Remove up to two last zombies on Satellite Instance upgrade.
      * Rename profiles to avoid confusion between Commons 2 and Commons 3.
      * Run drush @hostmaster hosting-dispatch during upgrade to sync things.
      * Send also OK report when running in the silent mode.
      * Set correct default DNS entry in /etc/hosts before running local install.
      * Shell: Fix for too restrictive Drush commands filtering.
      * Shell: Fix the broken Git support over SSH.
      * Shell: Fixed too restrictive permissions on the extra Drush directories.
      * SQL: Do not run the purge_binlogs script when binary logging is disabled.
      * SQL: Improve sqlmagic converter and allow it to use control files.
      * SQL: The sqlmagic_convert should not be available for extra lshell users.
      * SQL: Tune also key_buffer_size by default.
      * Sync generating secure passwords also for limited shell users.
      * Update csf.conf template.
      * Update self-healing for Tomcat/Jetty support.
      * Update welcome e-mail template to better explain how to manage databases.
      * Use Boost with silenced false alarms.
      * Use Limited Shell branch with fixed tab completion.
      * Use public DNS during pdnsd (re)installation to avoid issues.
      * Whitelist /tmp/make_tmp.* in the csf.fignore to avoid false alarms.


 You can read full changelog as always at: http://bit.ly/newboa

Enjoy!