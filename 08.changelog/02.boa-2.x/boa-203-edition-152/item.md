---
# http://learn.getgrav.org/content/headers
title: BOA-2.0.3 Edition
slug: boa-203-edition-152
menu: BOA-2.0.3 Edition
date: 17-05-2012
published: true
publish_date: 17-05-2012
# unpublish_date: 17-05-2012
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.0.3 – the biggest Edition ever, which includes many new features, 8 new platforms, 17 updated platforms, new Drupal core versions and many fixes and improvements introduced in the last three months since previous Edition.

 
    ### Stable Edition BOA-2.0.3
    ### Date: Thu May 17 18:17:40 EST 2012
    ### Installs Aegir 2.0.3 compatible with Aegir 1.9
    
    # There are major improvements and new features added in this BOA Edition.
    
      Here is the description of those most important/expected, while complete
      list of all changes, new features and fixes is available further below.
    
      * Caching backend has been simplified. We no longer use chained cache
        system with Memcached+Redis+database. New system uses only Redis cache
        and the same configuration for all Drupal 6 and Drupal 7 platforms.
        This new system doesn't require any extra module to be enabled in any site.
        Complete integration is already enabled by default for every platform/site
        installed by default and for every custom platform as before - the next
        day after first site on the custom platform has been created.
        You can disable this caching layer using the same modules/cache/NO.txt
        control file as before. While there is just one cache engine (Redis) used,
        there is also an automatic, instant failover to standard database caching,
        just in case Redis is not available for some reason. You can also disable
        Redis cache on the fly for debugging by adding ?noredis=1 to any URL.
        
      * We have added support for Drupal 8.x while still using modified
        Drush 4.6-dev version, so we can still support Drupal 5 on the same
        system, but on another Octopus instance.
      
      * You can choose different PHP version for PHP-FPM (web access)
        and PHP-CLI, for even greater control over compatibility with
        various Drupal major versions.
        
      * You can choose both PHP-FPM and PHP-CLI versions per Octopus instance,
        on the same system. And you can change those versions on upgrade.
    
      * Installing and upgrading BOA system has been greatly simplified.
        You can still configure and run both installers as before,
        but you can also use these new, shockingly simple command line tools
        to install Barracuda and Octopus at once, to install more Octopus
        instances, to run selective or batch upgrades of all Octopus instances etc.
        See docs/INSTALL.txt and docs/UPGRADE.txt for details.
    
      * We have added an 'easy install' configuration shortcuts for both
        standard (public) and localhost installs. You no longer need
        to read, understand and configure all options, unless you prefer
        to choose some non-default configuration options.
    
      * Default installs on Debian Squeeze and Ubuntu Precise use
        packages for PHP 5.3, so initial setup takes just 10-15 minutes.
    
      * You can easily grant limited shell and FTPS access for developers,
        simply by creating "Clients" in the Aegir control panel and define
        them as 'owners' of one or more sites. Their access will be limited
        to only sites they can manage, but only if you will send them their
        access credentials, which are independent of their Aegir control
        panel credentials and stored in the ~/users/ directory in your main account.
        You will find there files with passwords for every "Client" with at least
        one site attached. For example ~/users/o1.username file means that
        this Client's username for SSH and FTPS access is 'o1.username' while
        his password is stored in this file. This means that SSH/FTPS access
        is not granted automatically, but you can decide who should receive it.
        How to change any extra user's password? Simply delete his file
        ~/users/o1.username and wait up to 5 minutes - the system will re-create
        his account with new password. And how to delete the user completely?
        Simply delete this user "Client" account in the Aegir control panel and
        allow the system to delete also his SSH/FTPS access in the next 5 minutes.
    
      * We have added segfault monitor for php-fpm and nginx, enabled by default.
        It is pretty aggresive, because it disables vhost of any site causing
        segfault errors and sends e-mail alert to the Octopus instance owner
        and server owner e-mail addresses. Simple site re-verify in Aegir enables
        the site again - but until the next segfault only, so read the info
        included in the e-mail alert message, if this will happen. If you prefer
        to not run this monitor: `rm -f /var/xdrago/monitor/check/segfault_alert`
    
      * Previously recommended site and platforms re-verify on Clone or Migrate
        is now fully automated. Aegir will run these extra tasks as a part
        of Clone or Migrate task, to make sure that there are no errors
        and that Aegir is using up-to-date information collected about
        platforms and sites. It also automatically fixes the known problem
        with domain aliases incorrectly written in the original and cloned sites,
        as reported in the Aegir queue: http://drupal.org/node/1004526
      
      * Apps are now fully supported. If the App is not downloaded yet, installing
        it via browser only requires write permissions, normally never available
        for the web server user, so you need to create an empty control file, either
        in sites/all/modules/apps-allow.info or sites/domain/modules/apps-allow.info
        and then run 'Reset password' task. It will open write access where required
        until the next site 'Verify' task will run . After installing the App,
        remember to re-Verify the site to restore default, safe permissions.
    
      * Custom local.settings.php file support uses similar logic with control file
        sites/domain/modules/local-allow.info and also 'Reset password' task.
        After running this task the local.settings.php file will be group writable,
        so you will be able to edit it also when logged in as limited shell user.
        Remember to run site Verify when done, to restore safe permissions.
        Note that this file is created automatically, but is not open for write
        access by default.
        
    # Notes on new and updated platforms and new Drupal core:
    
      All 6.x and 7.x platforms have been updated with latest core,
      so they are all in fact new in this BOA Edition, but we list here
      only really new platforms or those with new version released
      since last BOA Edition, with one exception: we list also basic
      6.26.2 and 7.14.2 platforms as new.
    
      NOTE: before you will try to upgrade any of your sites,
      please read our important how-to:
    
      http://omega8.cc/the-best-recipes-for-disaster-139
      http://omega8.cc/are-there-any-specific-good-habits-to-learn-116
      http://omega8.cc/managing-your-code-in-the-aegir-style-110
    
      REALLY, PLEASE READ IT TO AVOID SOME HEAVY HEADACHES!
    
    # New Octopus platforms:
    
      CiviCRM 4.1.2-d6 ------------- http://civicrm.org
      CiviCRM 4.1.2-d7 ------------- http://civicrm.org
      Drupal 7.14.2 ---------------- http://drupal.org/drupal-7.14
      Drupal 8.0-dev --------------- http://bit.ly/drupal-eight
      MartPlug 1.0-beta1b ---------- http://drupal.org/project/martplug
      Octopus Video 1.0-alpha6 ----- http://octopusvideo.org
      Panopoly 1.0-beta3 ----------- http://drupal.org/project/panopoly
      Pressflow 6.26.2 ------------- http://pressflow.org
    
    # Updated Octopus platforms:
    
      Acquia 6.26.2 ---------------- http://bit.ly/acquiadrupal
      CiviCRM 3.4.8-d6 ------------- http://civicrm.org
      CiviCRM 4.0.8-d7 ------------- http://civicrm.org
      Commerce 1.7.1 --------------- http://drupalcommerce.org
      Commons 2.6 ------------------ http://acquia.com/drupalcommons
      Feature Server 1.1 ----------- http://bit.ly/fserver
      Managing News 1.2.2 ---------- http://managingnews.com
      NodeStream 1.5 --------------- http://nodestream.org
      NodeStream 2.0-beta1 --------- http://nodestream.org
      Open Atrium 1.4.1 ------------ http://openatrium.com
      Open Deals 1.0-beta7e -------- http://opendealsapp.com
      Open Outreach 1.0-rc1 -------- http://openoutreach.org
      OpenChurch 1.10-alpha1 ------- http://openchurchsite.com
      OpenPublish 3.0-alpha8 ------- http://openpublishapp.com
      Ubercart 2.9.1 --------------- http://ubercart.org
      Ubercart 3.1.1 --------------- http://ubercart.org
      Videola 1.0-alpha3 ----------- http://videola.tv
    
    # New features:
    
      * Add Adaptive Image Styles support.
      * Add Compass compatibility in the limited shell (Compass is not installed).
      * Add ssh-copy-id and ssh-add commands as allowed over SSH.
      * Add X-Speed-Cache-Key header for Speed Booster debugging.
      * All Clone/Migrate forms in the Aegir control panel have useful inline help.
      * Allow to easily re-start failed install by running boa installer again.
      * Allow to install PHP 5.3 only with option _PHP_MODERN_ONLY=YES (default).
      * Deny HTTPS access on Nginx level for all known bots and crawlers.
      * Do not force HTTPS for Aegir if /data/conf/no-https-aegir.inc file exists.
      * Fix system time hourly via auto-healing.
      * Install wkhtmltopdf by default - available at /usr/bin/wkhtmltopdf
      * Issue #1263602 - New Relic Server and Apps Monitor with per Site reporting.
      * Issue #1392498 - Use .barracuda.cnf to define YES/NO for config overrides.
      * Issue #1428078 - Compatibility with resp_img module.
      * Issue #1436522 - Add option to set _PHP_CLI_VERSION.
      * Issue #1438906 - Add Imagick to PHP by default.
      * Issue #1463494 - Add support for radioactivity module.
      * Issue #1542712 - Automated wildcard DNS for easy localhost mode.
      * Lock temporarily almost all known crawlers on high load with error 503.
      * Make _NGINX_DOS_LIMIT configurable and allow higher load by default.
      * Make both 1 and 5 minute max allowed load configurable in the auto-healing.
      * Support for automatically managed extra SSH/FTPS accounts per Aegir Client.
      * The _LOAD_LIMIT used in the auto-healing system is now configurable.
      * The _SPEED_VALID_MAX used as a Speed Booster cache TTL is now configurable.
      * Ubuntu Precise 12.04 is fully supported.
      * Use nice default /root/.bashrc config.
      
    # New Aegir modules or extensions:
    
      * Add hosting_advanced_cron module - enabled by default.
      * Add hosting_civicrm_cron module - enabled by default.
      * Add hosting_task_gc module - enabled by default.
      * Add provision_cdn module and extension, by default not enabled.
      * Add remote_import and hosting_remote_import - not enabled by default.
      * Add revision_deletion module - configured and enabled by default.
      * Registry Rebuild Drush extension - installed by default.
    
    # New o_contrib modules:
    
      * entitycache-7.x-1.x-dev
      * nocurrent_pass-7.x-1.0
      * speedy-7.x-1.0
    
    # Changes:
    
      * Acquia 7.x platform has been merged with Ubercart 3.
      * Always disable css_gzip, javascript_aggregator and performance modules.
      * Automate database server secure setup on initial install.
      * Disable /etc/cron.daily/mlocate by default.
      * Do not disable update module - it may break some features depending on it.
      * Do not enable filefield_nginx_progress module by default.
      * Do not remove Testing profile and use better naming convention for D7/D8.
      * Do not search for mirrors by default.
      * Drupal 8 compatible Drush 4.6-dev
      * GitHub availability is required also when another mirror is used by default.
      * Installing Git from sources is now optional.
      * Limited shell 0.9.15.1-sec-noreload
      * Lower default APC and Redis memory in VZ to 64MB to avoid known VZ issues.
      * MariaDB and Percona 5.5
      * Modify Ubercart platform to include some contrib modules in the D6 version.
      * Nginx 1.3.0
      * Open Enterprise 1.0-beta3 is deprecated and not supported.
      * Plain FTP access disabled with FTPS-only mode available.
      * Pure-FTPd server install is now optional, but still default.
      * Send all known bots to $args free URLs.
      * Use _HTTP_WILDCARD=YES by default to match Aegir standard setup.
    
    # Fixes:
    
      * Abort all parent installers as soon as any sub-installer fails.
      * Add $http_x_forwarded_proto to the cache key to never mix HTTP and HTTPS.
      * Add a list/chart in the readme for an easy overview of all included modules.
      * Add volatile updates to /etc/apt/sources.list for Squeeze.
      * All connection tests should be run after netcat is installed.
      * Allow more than one IP to connect to the same FTPS account at the same time.
      * Allow some known php files also in profiles - a fix for config regression.
      * Always update nginx_speed_purge.conf file on upgrade.
      * Archive install and upgrade logs in /var/backups/
      * Avoid double dots in $cookie_domain.
      * Better detection of real visitor IP in the scan_nginx abuse guard.
      * Cache 403 response for 5s by default.
      * Count only valid requests in the scan_nginx abuse guard.
      * Disable caching in admin_menu module by default.
      * Disabled allow_url_fopen breaks drush dl.
      * Do not allow bots to create cache entries with long expire time.
      * Do not prompt for D6 or D7 vanilla platforms install if not defined.
      * Explain in the e-mail templates that plain FTP is no longer available.
      * Fix cart block issue in Ubercart.
      * Fix for Debian Lenny support - packages have been moved to archives.
      * Fix for slow networks/DNS in pdnsd cache default config.
      * Fix for VServer on _LENNY_TO_SQUEEZE upgrade.
      * Fix tune_memory_limits logic to really tune the config on low mem systems.
      * Follow some symlinks when running chmod/ownership repair daily.
      * Force global upgrade for Expire and Purge modules.
      * Force safe default settings for expire module.
      * Improved Lenny to Squeeze major upgrade support.
      * Increase allowed limit_conn for local purge requests.
      * Issue #1216420 - Incorrect lshell path in /etc/passwd breaks FTPS on Squeeze.
      * Issue #1317264 #1543118 - Uninstall Sendmail if exists.
      * Issue #1377492 - Improve Install/Upgrade mode detection and delete zombies.
      * Issue #1398050 - Use our mirror for all downloads on install and upgrade.
      * Issue #1436522 - Add missing php.ini for PHP-CLI 5.3
      * Issue #1440796 - Aegir support broken due to duplicate db update in Commons.
      * Issue #1441366 - The _USE_SPEED_BOOSTER switch is deprecated.
      * Issue #1443284 - Early start of CSF may lockout the ssh user.
      * Issue #1445460 - Broken Git install on Ubuntu Lucid.
      * Issue #1451262 - Do not lock the access to phpinfo.
      * Issue #1472460 #1524738 - Nginx denies: PUT, DELETE and OPTIONS.
      * Issue #1475416 - Unable to install Barracuda due to Aegir failed install.
      * Issue #1478984 - Add Access-Control-Allow-Origin header with wildcard.
      * Issue #1479188 - Octopus does not respect _DNS_SETUP_TEST setting on upgrade.
      * Issue #1505370 - Conflict between Mime Type and Document Type in Nginx.
      * Issue #1515762 - Nginx microcaching should skip all known AJAX requests.
      * Issue #1526382 - The _PHP_CLI_VERSION set in cnf file is not respected.
      * Issue #1527852 - WSOD on D7 sites with Redis enabled for anonymous visitors.
      * Issue #1528692 - Both cache_backport and redis modules not added on upgrade.
      * Issue #1528726 - Redis caching should be unified across all instances.
      * Issue #1528996 - Nginx cache should use TTL 1s only for upstream errors.
      * Issue #1534306 - Duplicate directives break Dotdeb Nginx version.
      * Issue #1539512 - Keep custom Redis configuration during upgrade.
      * Issue #1540112 - HEAD install fails on Debian Squeeze 32bit.
      * Issue #1540242 - Add useful codecs to ffmpeg if enabled.
      * Issue #1541334 - Add kvm to supported virtualization systems.
      * Issue #1544144 - Use $server_name instead of $host in all sites/ paths.
      * Issue #1547878 - Port 11371 should be open for outgoing connections.
      * Issue #1553150 - Both php.ini and my.cnf config files overridden on upgrade.
      * Issue #1553166 - Disable incompatible mysql config options.
      * Issue #1554972 - PHP cli downgraded to 5.2 on upgrade.
      * Issue #1556192 - Upgrade Entity API to head to fix issue with Drupal 7.14
      * Issue #1585348 - Disable openchurch_video_demo_content to avoid fatal error.
      * Kill nash-hotplug if running.
      * Lower some my.cnf defaults to better support low mem systems.
      * Make default myisam_sort_buffer_size big enough to run repair if required.
      * Make sure that /dev/null has correct permissions.
      * Pass some expected headers when using local proxy.
      * Remind people that they should use their own e-mail address or exit early.
      * Remove deprecated Nginx config includes.
      * Sanitize important variables early.
      * Save 330 seconds with 3x faster spinner.
      * Set hosting_queue_cron_frequency to 8888 weeks by default to use schedule
        defined via hosting_advanced_cron module and never override it.
      * Share and symlink civicrm code.
      * Skip _AEGIR_LOGIN_URL in the debug mode - it is empty then.
      * Update mime.types for Nginx.
      * Use _FULL_FORCE_REINSTALL when recovering from broken/partial install.
      * Use faster locations matching where possible in the Nginx config.
      * Use higher values for limit_conn in Nginx to avoid issues when required.
      * Use loglevel warning in Redis config.
      * Use safe placeholders to avoid issues on low-mem machines.


 You can read full changelog as always at: http://bit.ly/newboa

Enjoy!