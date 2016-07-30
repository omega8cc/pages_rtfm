---
# http://learn.getgrav.org/content/headers
title: BOA-2.0.4 Edition
slug: boa-204-edition-231
# menu: BOA-2.0.4 Edition
date: 08-11-2012
published: true
publish_date: 08-11-2012
# unpublish_date: 08-11-2012
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

 We are happy to release BOA-2.0.4 Edition, which includes many new features, 1 new platform, 19 updated platforms, new Drupal 7 core version and many, many fixes and improvements introduced in the last six months since previous Edition.

 
    ### Stable Edition BOA-2.0.4
    ### Date: Thu Nov  8 18:31:01 EST 2012
    ### Installs Aegir 2.0.4 compatible with Aegir 1.9
    
    # New Octopus platforms:
    
      Commerce 2.0-rc4 ------------- http://drupalcommerce.org
    
    # Updated Octopus platforms:
    
      CiviCRM 4.1.6-d6 ------------- http://civicrm.org
      CiviCRM 4.2.6-d7 ------------- http://civicrm.org
      Commerce 1.11.1 -------------- http://drupalcommerce.org
      Commons 2.10 ----------------- http://acquia.com/drupalcommons
      Conference 1.0-rc2 ----------- http://usecod.com
      Drupal 7.17.1 ---------------- http://drupal.org/drupal-7.17
      Drupal 8.0-dev-tested -------- http://bit.ly/drupal-eight
      ELMS 1.0-beta1 --------------- http://elms.psu.edu
      NodeStream 1.5.1 ------------- http://nodestream.org
      NodeStream 2.0-beta8 --------- http://nodestream.org
      Open Atrium 1.6.1 ------------ http://openatrium.com
      Open Deals 1.11 -------------- http://opendealsapp.com
      Open Outreach 1.0-rc6 -------- http://openoutreach.org
      OpenChurch 1.11-beta5 -------- http://openchurchsite.com
      OpenPublish 3.0-beta7 -------- http://openpublishapp.com
      OpenScholar 2.0-rc1 ---------- http://openscholar.harvard.edu
      Panopoly 1.0-rc2 ------------- http://drupal.org/project/panopoly
      Ubercart 2.10.1 -------------- http://ubercart.org
      Ubercart 3.2.1 --------------- http://ubercart.org
    
    * We plan to shorten BOA system release and upgrades cycle
      to 1-2 months max, so we have decided to remove support for some
      outdated distros. We have tried to manage both security and version
      updates for some abandoned or semi-abandoned distros, to keep them
      useful for you, but since it involves increasing amount of work
      because of cascades of no longer compatible patches and various
      dependencies, we have decided that it is time to stop doing it,
      if their original maintainers no longer care about their users.
    
      Here is a list of distros we no longer support:
    
      MartPlug ------------ http://drupal.org/project/martplug
      Octopus Video ------- http://octopusvideo.org
      Open Academy -------- http://drupal.org/project/openacademy
      Open Enterprise ----- http://drupal.org/project/openenterprise
      OpenPublic ---------- http://openpublicapp.com
      Videola ------------- http://videola.tv
    
      The platforms listed above can be re-added when their maintainers
      will fix all critical issues and/or apply required updates.
    
    # New features:
    
      * Add auto-healing support for Bind9.
      * Add LOCK/FROZEN check for PHP-FPM and Tomcat in the auto-healing.
      * Add option to force 15min Speed Booster cache TTL for anonymous visitors.
      * Add optional easy install of already supported Compass Tools.
      * Add support for aegir|platforms|both modes on octopus upgrade.
      * Allow for another one upgrade daily but only to add more platforms.
      * Allow to install unsupported distros with option _ALLOW_UNSUPPORTED=YES
      * Allow to install vanilla Aegir 2.x and Drush 5.7 with "stock" option.
      * Improved databases backup with added OPTIMIZE TABLE foo action per table.
      * New Relic PHP Agent version 3.0 compatibility.
      * Pseudo-streaming server-side support for Flash Video (FLV) and H.264/AAC.
      * Support for Wysiwyg Fields module.
    
    # New Aegir modules or extensions:
    
      * Add hosting_tasks_extra module and provision_tasks_extra extension.
    
    # New o_contrib modules:
    
      * Add login_security module in D7 contrib.
      * Add cdn module in both D6 and D7 contrib.
    
    # Changes:
    
      * Allow outgoing mysql connections by default.
      * APC 3.1.13
      * Chive 1.2
      * Do not bundle seckit module in o_contrib.
      * Do not enable Expire and Purge modules by default.
      * Enable Syslog module by default.
      * Git 1.8.0
      * MariaDB 5.3.9 on Debian Lenny
      * MariaDB 5.5.28
      * Nginx 1.3.8
      * Percona 5.5.28
      * PHP 5.3.18
      * Pure-FTPd 1.0.36
      * Redis 2.6.4
      * Remove not supported httprl module and disable if enabled.
      * The filefield_nginx_progress is forced-enabled in all D7 sites, again.
      * Use PHP-FPM 5.3 for Chive, Collectd and other non-Drupal sites.
      * Use php-cli 5.3 for drush on command line by default.
        You can still force 5.2 with --php=/usr/local/bin/php drush option.
    
    # Fixes:
    
      * Add cache_tax_image bin to no-redis-cache exceptions.
      * Add support for pdnsd in the VServer guest.
      * Allow all standard compass/sass commands in limited shell.
      * Auto-discover _NEWRELIC_KEY if not listed in .barracuda.cnf
      * Better auto-healing for php-fpm zombies edge case.
      * Better check for failed login attempts (when user exists).
      * Better permissions magic repair running daily.
      * Deny crawlers on search results pages - they may cause very high load.
      * Disable spinner if screen is used.
      * Do not force default Debian and Ubuntu mirrors even if _AUTOPILOT=YES.
      * Do not quote password in .my.cnf - it breaks mytop.
      * Do not use log/custom_cron for anything.
      * Do not use resolveip in the localhost mode.
      * Exclude cache_bootstrap and cache_pulled_tweets from Redis caching.
      * Fix for broken drush make edge case caused by leftovers.
      * Fix for broken Tika download URL.
      * Fix for civicrm_engage in D6.
      * Fix for Debian Lenny upgrade.
      * Fix for global.inc logic related to high traffic sites only.
      * Fix for NGX, PHP and SQL forced reinstall mode.
      * Fix for Pin-Priority in Squeeze.
      * Fix for sql abuse monitor.
      * Fix for the selectively forced upgrade mode.
      * Fix motd for Skynet fun.
      * Fix too restrictive lshell command filtering.
      * Force Pure-FTPd rebuild on every upgrade to avoid broken binary.
      * Force tomcat restart and reload php-fpm hourly.
      * Improve Domain module support.
      * Improve mysql crashed tables detection and repair in auto-healing.
      * Improve Nginx Abuse Guard by stopping those never cached POST DoS attacks.
      * Improve Nginx guard support for VServer guests.
      * Improved checkpoint info in Octopus.
      * Issue #1225380 - Do not truncate sessions table during db daily backup.
      * Issue #1472786 - SQL check ERROR and too many SQL check CLEAN notices.
      * Issue #1528726 - Fix for Redis support in all shared directories/code.
      * Issue #1540242 - Do not install conflicting libavcodec53 or libavcodec52.
      * Issue #1588060 - Make sure that /var/run is present in open_basedir.
      * Issue #1589052 - Incomplete PATH breaks standard tasks.
      * Issue #1590120 - Fix for java path changed in recent Ubuntu releases.
      * Issue #1591746 - Update GeoIP.dat file automatically.
      * Issue #1592646 - Enabled old cache backend integration module causes WSOD.
      * Issue #1592650 - Do not use Hide platforms with non-default profiles.
      * Issue #1592680 - Upload progress module breaks uploads on all D7 sites.
      * Issue #1593794 - New redis-only caching backend settings.
      * Issue #1593810 - Duplicate php-cli 5.3 binaries after upgrade.
      * Issue #1593980 - Remove invisible characters breaking localhost install.
      * Issue #1597580 - External/Aggressive caching in D6 breaks path_alias_cache.
      * Issue #1598676 - Collectd graphs broken.
      * Issue #1600426 - Cron is run every minute on all sites not yet defined.
      * Issue #1602142 - Do not use device specific keys for Redis cache entries.
      * Issue #1606146 - The manage_ltd_users.sh script locks important tasks.
      * Issue #1614162 - CRON Not Running on Octopus Satellites and Sites.
      * Issue #1643616 - APC is missing in the Ubuntu Precise based install.
      * Issue #1659452 - Add support for Aegir HTTPS header in the Speed Booster.
      * Issue #1663262 - fix FMG install on Ubuntu Precise.
      * Issue #1679114 - New user name check in Octopus is too restrictive.
      * Issue #1689656 - Avoid caching /civicrm* and known webform requests.
      * Issue #1716004 - The zlib.output_compression should be disabled in 5.3
      * Issue #1728616 - Better CDN Far Future expiration support.
      * Issue #1777982 - Do not break wordpress_migrate module support.
      * Issue #1778712 - Better workaround for MariaDB 5.5.27 critical bug.
      * Issue #1784440 - Cannot stat scan_nginx when using BOND.sh.txt
      * Issue #1796420 - Do not break write access to the tcpdf cache directory.
      * Issue #1798288 - Provision-backup_delete could not be found.
      * Issue #1799116 - Standardize on installation vs. install profile.
      * Issue #1821866 - Force Nginx rebuild to include pseudo-streaming support.
      * Issue #1824888 - BOND.sh.txt breaks Nginx, SQL and PHP configuration.
      * Issue #1825298 - Redis: force rebuild from sources on version mismatch.
      * Issue #1825420 - Avoid the Use of undefined constant OctopusNoCacheID.
      * Issue #1825630 - Remove duplicate code causing false alarm.
      * Issue #1825992 - Redis cache is never cleared via php-cli.
      * Issue #1825998 - Improved auto-healing for Redis.
      * Issue #1835796 - Default cache headers break CloudFlare Always Online.
      * Make sure that path_alias_cache module takes precedence.
      * Make sure that PHP 5.2 is re-installed if required.
      * Monitor and kill too long running sites cron tasks.
      * Move away buagent init script if exists when Barracuda runs.
      * Nginx: Allow to include high level local configuration override.
      * Nginx: Better regex for exceptions in the abuse guard monitor.
      * Nginx: Block stupid spiders/downloaders with 403 error, not CSF.
      * Nginx: Deny known bots on some heavy URLs.
      * Nginx: FileField Nginx Progress 7.x-2.3 compatibility.
      * Nginx: Fix for broken images paths in civicrm.
      * Nginx: Fix for D6 upload progress support.
      * Nginx: Make the abuse monitor aware of possible lang code prefixes.
      * Nginx: Monitor and block if required also via-multi-proxy attacks.
      * Nginx: Remove packages on every upgrade to avoid duplicate re-installs.
      * Nginx: Remove redundant URL filtering.
      * Nginx: Send 403 for vbulletin URI to avoid Drupal heavy 404.
      * Nginx: Support for /contrib/ for wysiwyg helpers exceptions location.
      * Nginx: Use latest nginx-upload-progress-module v0.9.0
      * Nginx: Use ngx_cache_purge-1.6
      * PHP: Allow short_open_tag also in 5.3
      * PHP: Disable the original php5-fpm init script causing segfaults.
      * PHP: Fix for _FROM_SOURCES PHP-FPM 5.3 build.
      * PHP: Fix for the php53-fpm init script.
      * PHP: Force proper php53-fpm restart if required.
      * PHP: Install JSMin extension by default.
      * PHP: Install php-pear by default also in no-src based default install.
      * PHP: Load extensions in a safe, correct order.
      * PHP: Log killed php-fpm events.
      * PHP: Make sure that all builds use correct, fresh downloads.
      * PHP: Make sure that php53-fpm is disabled during apt-get based upgrade.
      * PHP: Make sure that suhosin.so is removed and jsmin.so added.
      * PHP: Remove duplicate and conflicting allow_call_time_pass_reference.
      * PHP: Remove php5-sasl extension causing segfaults.
      * PHP: Remove php5-suhosin from the stack - too many weird issues.
      * PHP: The realpath_cache_ttl should be as low for CLI as possible.
      * PHP: Use 2x higher limits in the tune_web_server_config logic.
      * Purge Redis cache hourly.
      * Randomize runner intervals.
      * Remove all control files on init to avoid aborted Octopus upgrades.
      * Remove any extra search directive from resolv.conf when pdnsd is installed.
      * Remove Dotdeb libmysqld-dev conflicting with Percona libmysqlclient-dev.
      * Remove not really working properly Boost separate mobile bins.
      * Remove not supported MTA only on initial install.
      * Remove old cache module from all old profiles.
      * Segfault monitor should not disable sites by default.
      * Serve .less files as static by default, no log.
      * Set hosting_advanced_cron_default_interval to 3 hours.
      * SQL: Use skip-name-resolve by default.
      * Support both HTTP_X_FORWARDED_PROTO and HTTPS.
      * The dev. should not disable Redis cache.
      * The missing /usr/bin/lshell entry may affect also Lucid.
      * There is no need to force Debian mirror.
      * Tune AdvAgg config - disable async mode and use JSMin by default.
      * Use autoselect for civicrm downloads.
      * Use DrupalDatabaseCache for some Redis bins to avoid confirmed issues.
      * Use higher default timeouts for php-cli and wait_timeout in mysql.
      * Use SERVER_NAME instead of HTTP_HOST header in the Redis cache key.
      * Use version specific directory for static downloads.
      * Yet another umask trick for shell and SFTP.


 You can read full changelog as always at: http://bit.ly/newboa

Enjoy!