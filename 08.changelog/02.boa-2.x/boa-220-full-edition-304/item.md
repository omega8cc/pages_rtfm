---
# http://learn.getgrav.org/content/headers
title: BOA-2.2.0 Full Edition
slug: boa-220-full-edition-304
menu: BOA-2.2.0 Full Edition
date: 30-03-2014
published: true
publish_date: 30-03-2014
# unpublish_date: 30-03-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.2.0 Full Edition, which includes a giant list of new features, improvements, fixes, new and updated Octopus platforms, and is a result of a few months of creative development, supported by helpful feedback from the Drupal and BOA community. Many Thanks to All of You!

 
    ### Stable BOA-2.2.0 Release - Full Edition
    ### Date: Mon Mar 31 06:44:08 SGT 2014
    ### Includes Aegir 2.x-boa-custom version.
    
    # Release Notes:
    
      There are many important changes and improvements in this release
      you should be aware of *before* running your BOA system upgrade.
    
      Even if you are on a hosted BOA system with upgrades managed for you,
      it is very important to read at least this extensive release notes.
    
      Here is a list of topics covered in detail further below:
    
      * New 'legacy' mode available for installs and upgrades
      * Important Note For Those Using Our Hosted Aegir Service!
      * Custom php.ini protection has changed and will not honor old settings
      * Barracuda no longer supports Percona since 2.2.0 release
      * Support for PHP FPM/CLI version safe switch per Octopus instance
      * All PHP FPM workers in 5.5, 5.4 and 5.3 now use the 'ondemand' mode
      * Drush aliases are now automatically copied to all relevant accounts
      * Drush is now restricted to use only trusted modules installed by default
      * The ~/.drush and other important directories and symlinks are protected
      * Support for safely configurable cache bins exceptions in Redis
      * Two-Factor-like Authentication to protect access to Chive DB Manager
      * Support for session.cookie_lifetime configurable via INI files
      * Support for files permissions-fix exceptions via platform level INI file
      * High-performance JavaScript callback handler (js) in all platforms
    
      And if you are more curious, read also the big changelog further below,
      which covers only a small number of over 560 commits since BOA-2.1.3 release.
    
      But what if you are not ready for this major upgrade and you would like
      to have more time for testing, but still be able to run system upgrades,
      thus effectively still using previous version 2.1.3 with standard command
      'barracuda up-stable system', as explained in the docs/UPGRADE.txt?
    
    #-### New 'legacy' mode available for installs and upgrades
    
      We are introducing special 'legacy' mode both for BOA installs and upgrades.
    
      This means that starting with BOA-2.2.0 you can use commands like:
    
      $ boa in-legacy public server.mydomain.org my@email o1
      $ barracuda up-legacy system
      $ octopus up-legacy o1
      etc.
    
      These special 'legacy' commands allow you to install and/or upgrade the 'old
      stable', once the 'new stable' is released. But only until another 'stable'
      is released, of course. Thus you can use it only as an interim solution
      if you are not yet ready for latest 'stable' BOA Edition, for any reason,
      but you want to update at least the low level system packages, kernel etc.
    
      Note also that if you will upgrade to current 'stable', it is not possible
      to downgrade back to the 'old stable' with 'legacy' mode, so please proceed
      with care!
    
      This option will be particularly important once we release *next* major BOA
      Edition. It will come with terminated support for Drush 4, Drupal 5 and, yes,
      PHP 5.2 (finally). This step is required to use latest Drush 6+ with supported
      Drupal cores versions and supported PHP versions, which in fact is required
      to introduce the real Aegir 2.0 in BOA -- we are still using older, customized
      for backward compatibility, Aegir 2 HEAD version, so it is time to move on and
      stay up to date with everything, get new features like ability to manage
      Drupal sites in subdirectories etc.
    
      Once that *next* major BOA Edition is released, we will freeze the 'legacy'
      mode at 2.2.x series level, which will receive only security upgrades and
      no further feature nor bugfix releases. At that point you will have to stick
      to the 'legacy' BOA version if you will need to run PHP 5.2 and Drupal 5
      with Aegir based on Drush 4. It will be still possible, but not recommended
      and not really supported, besides security related issues outside of Drupal.
      This also means that at that point the 'legacy' version will no longer
      receive Drupal core upgrades, even if there will be security core releases.
    
      Note that we don't use the term "major release" in the known convention
      for versions naming. It is because the first digit, for historical reasons,
      refers to the Aegir version supported, the second digit refers to BOA stack
      major release, and the last digit refers to both feature and bugfix BOA
      stack upgrades.
    
    #-### Important Note For Those Using Our Hosted Aegir Service!
    
      NOW is the time (and last chance) to upgrade all your legacy Drupal 5 sites
      and outdated Drupal 6 sites still not compatible with at least PHP 5.3,
      because once we upgrade to the *next* major BOA Edition, it will be no longer
      possible to still run Drupal sites not compatible with PHP 5.3 -- there
      were literally years of this legacy support provided, and this finally
      comes to the end, because we will not use the BOA 'legacy' mode on our own
      servers. It will be still available for remotely managed 'Aegir on Your Own
      Server' option, though, but only on request: https://omega8.cc/support
    
    #-### Custom php.ini protection has changed and will not honor old settings
    
      If you have custom settings in any of your php.ini files protected with
      old variable in the /root/.barracuda.cnf, make a backup of your ini files
      before running this upgrade. While these files will not get overwritten,
      they will no longer be used, because we have introduced new, standardized
      directory structure to properly support multi-PHP-versions systems.
    
      Respective php.ini files are now located in /opt/phpXX/etc/phpXX.ini
      for FPM and /opt/phpXX/lib/php.ini for CLI, where XX is 55, 54, 53 or 52,
      depending on the versions listed via _PHP_MULTI_INSTALL variable in the
      /root/.barracuda.cnf file. Also the variables used to protect ini files
      from being overwritten have changed to _CUSTOM_CONFIG_PHPXX.
    
      If you need any non-standard settings in any of active ini files, don't
      overwrite them with the old files, but rather carefully review and apply
      only the differences you need.
    
    #-### Barracuda no longer supports Percona since 2.2.0 release
    
      If you have used Percona before, Barracuda will force upgrade to MariaDB 5.5
      and PHP rebuild automatically. We plan to add possibility to install
      MariaDB 10.0 once released as stable and tested. MariaDB is the default
      DB server in Barracuda for a long time already.
    
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
    
      Note that the same version will be used in all platforms and all sites hosted
      on the same Octopus instance. Why not to try latest and greatest PHP 5.5 now?
    
    #-### All PHP FPM workers in 5.5, 5.4 and 5.3 now use the 'ondemand' mode
    
      This change will help to better manage memory use, especially on systems with
      multiple PHP versions running in parallel. This will also free resources
      and allocate them dynamically only when requests are coming and only to
      the active FPM pools. Note that the 'ondemand' mode doesn't affect Zend
      OPcache, because it is managed by the parent process(es) which stay(s) active.
    
      The net result is that on a vanilla BOA install, without non-hostmaster sites
      running, the complete stack consumes just ~200 MB of RAM (in total, so with
      MariaDB, Redis and Nginx etc. included) with all three PHP-FPM versions
      running in parallel: 5.5, 5.4 and 5.3:
    
      CPU[#*                                                       2.0%]
      Mem[|||||||||||||###***********************************209/1002MB]
      Swp[                                                        0/0MB]
    
      magic:~# ps axf | grep fpm
       8380 ? Ss 0:00 php-fpm: master process (/opt/php55/etc/php55-fpm.conf)
       8391 ? Ss 0:00 php-fpm: master process (/opt/php54/etc/php54-fpm.conf)
       8402 ? Ss 0:00 php-fpm: master process (/opt/php53/etc/php53-fpm.conf)
      magic:~#
    
    #-### Drush aliases are now automatically copied to all relevant accounts
    
      While Aegir manages Drush aliases for its backend needs, they are normally
      not available for the main nor the extra shell users on the instance.
    
      But starting with 2.2.0, BOA automatically manages copies of all Drush
      aliases, by adding them, updating or removing, every 5 minutes, once it
      detects that there are changes applied, like: the site has been migrated
      to another platform, or associated client/owner has been updated, etc.
    
      You no longer need to `cd` to the respective site directory to perform
      some available Drush tasks. Just check the available aliases list with
      `drush aliases` and then enjoy the beauty of `drush @foo.com command` syntax.
    
    #-### Drush is now restricted to use only trusted modules installed by default
    
      Note: this change affects only Aegir backend/system user, typically o1,
      while all other limited shell accounts are not affected, because they are
      already individually jailed with protected custom php.ini and special
      Drush wrappers and settings.
    
      This means that you can skip this section if you are on a hosted Aegir.
    
      Customized Drush now included in BOA by default, will be able to use only
      extensions/commands bundled with contrib modules which are either a part
      of modules added in every platform via shared o_contrib/o_contrib_seven
      symlink located in the platform core modules directory, or are included
      in the built-in platforms installation profiles space, or in the system
      account, protected .drush sub-directory.
    
      This means that any Drush extension/command bundled with contrib module
      uploaded to the sites/all/modules space in all built-in platforms will be
      ignored and not available on command line for the backend user. The same
      applies to site level contrib space, if used.
    
      Additionally, any Drush extension/command bundled with custom platforms
      located in the ~/static directory tree will be completely ignored by Drush,
      no matter where uploaded: core, profiles, sites/all or sites/foo.com space.
    
      This is not a problem in hosted environments, where users normally never
      should have an access to the Aegir backend user, anyway.
    
      If you have any reason to use Drush on command line as an Aegir backend/system
      user, for example to escape limited shell restrictions, we recommend to
      install vanilla Drush 6, for example in /opt/tools/drush/vanilla/drush/ and
      then symlink it into /usr/local/bin/ with custom name, so it will be available
      automatically in your backend o1 user's PATH.
    
      Further improvements to secure sites and instances in a completely locked
      virtual jails are planned in next BOA releases, which will address all other
      known and even potential security issues in Aegir.
    
    #-### The ~/.drush and other important directories and symlinks are protected
    
      There are directories, files and symlinks which should be protected from
      any changes and managed exclusively by the BOA system. The reasons may vary
      from security to avoidable support requests when the less experienced user
      will delete his sites or platforms symlinks, while they can't be easily nor
      automatically recreated. It also prevents the sub-accounts users from using
      their account home directory as a private upload/archive disk space.
    
    #-### Support for safely configurable cache bins exceptions in Redis
    
      Sometimes you may want to exclude some problematic cache bins from Redis
      so they will use default SQL engine, at least until related issue will be
      fixed either in your contrib code or in the Redis integration module.
    
      Normally you had to edit the local.settings.php file which is both tedious
      and dangerous because of extra steps: https://omega8.cc/node/230 to add
      a line, for example: $conf['cache_class_cache_foo'] = 'DrupalDatabaseCache';
      Plus, it had to be done for every site separately.
    
      Now you can simply list the cache bins to exclude, comma separated, either
      in the site or platform level active INI file.
    
      Example: redis_exclude_bins = "cache_views,cache_foo,cache_bar"
    
    #-### Two-Factor-like Authentication to protect access to Chive DB Manager
    
      We are introducing Two-Factor-like Authentication logic - now extended also
      to protect Chive DB Manager, Collectd Graph Panel and SQL Buddy DB Manager.
      You must be logged in via SSH and run any auto-continuos command, for example:
      `ping -i 30 google.com` to keep the access open for your IP address.
    
      Why is this important?
    
      While BOA forces HTTPS connection for Chive, anyone who knows the URL can
      access it and attempt to either run brute-force attack to get into your
      site's database, or at least attempt to hammer the server and cause DoS-like
      effects, at least until the system will block his IP on the firewall.
    
      The other important reason is that your site's DB credentials change only
      when you migrate or rename the site, and otherwise remain intact. Now, what
      if you have an employee or a freelancer whom you no longer want to be able
      to access your site? If you think that deleting his SFTP sub-account is
      enough, think again. He still can access your site's database via Chive, if
      he knows the site's DB credentials and the Chive URL.
    
      But now it's no longer possible. Only the visitor who is able to successfully
      authenticate himself via SSH, and keeps active SSH session, will be able
      to access the Chive URL. The rest of the world will see just dummy Nginx 403
      Access Denied error.
    
      And in case you are using self-hosted BOA, the same protection is applied
      also to Collectd Graph Panel and SQL Buddy DB Manager.
    
    #-### Support for session.cookie_lifetime configurable via INI files
    
      You can control session cookies expiration (TTL) per site and per platform.
      The value (in seconds) of the session_cookie_ttl variable is used as
      session.cookie_lifetime value.
    
      BOA default defined in the system level global.inc file is 86400 == 24h.
    
      We also recommend that you enable and configure built-in session_expire
      module, which allows you to keep the sessions DB table tidy. Make sure that
      TTL set via session_cookie_ttl variable is *lower* than TTL configured
      in the session_expire module, because the module does not care about PHP
      settings and simply deletes old entries from the sessions table on cron run.
    
    #-### Support for files permissions-fix exceptions via platform level INI file
    
      You can opt-out from globally enabled daily-permissions-fix procedure per
      platform with new fix_files_permissions_daily variable.
    
      This feature can be useful when you prefer to manage custom platform in
      a monolithic codebase mode in Git, so forcing permissions could conflict
      with your workflow or development tools. Otherwise you should never disable
      this to avoid issues with Aegir tasks related to sites on this platform.
    
      Note that the system level option _PERMISSIONS_FIX (introduced in BOA-2.1.0
      and set to NO by default) should be also enabled with YES in the system level
      /root/.barracuda.cnf file, if you prefer to have permissions fixed in all
      sites on all platforms, except those with fix_files_permissions_daily = FALSE
      set in the platform level, active INI file.
    
    #-### High-performance JavaScript callback handler (js) in all platforms
    
      All platforms, both built-in and custom in the ~/static directory tree, enjoy
      automatically added High-performance JavaScript callback handler (js) support,
      which requires extra /js.php file in the platform root and also proper Nginx
      rewrites. The module itself is also included in the built-in o_contrib bundle.
    
      All you need is to enable the module, if recommended by any other module,
      and enjoy much faster page generation, where possible. You can review the
      full list of modules which will benefit from this great helper module on its
      project page: https://drupal.org/project/js
    
    
      Enjoy another super-fast and even more powerful BOA Edition!
    
    
    # New Octopus platforms:
    
      ### Drupal 7.26.4
    
      Guardr 1.1 ------------------- https://drupal.org/project/guardr
    
    # Updated Octopus platforms:
    
      ### Drupal 7.26.4
    
      Commerce 1.24 ---------------- https://drupal.org/project/commerce_kickstart
      Commerce 2.13 ---------------- https://drupal.org/project/commerce_kickstart
      Commons 3.9.1 ---------------- https://drupal.org/project/commons
      Drupal 7.26.4 ---------------- https://drupal.org/drupal-7.26
      Open Academy 1.0 ------------- https://drupal.org/project/openacademy
      Open Atrium 2.15 ------------- https://drupal.org/project/openatrium
      Open Deals 1.32 -------------- https://drupal.org/project/opendeals
      Open Outreach 1.5 ------------ https://drupal.org/project/openoutreach
      OpenBlog 1.0-a3 -------------- https://drupal.org/project/openblog
      OpenChurch 1.12 -------------- https://drupal.org/project/openchurch
      OpenScholar 3.12.1 ----------- http://theopenscholar.org
      Panopoly 1.2 ----------------- https://drupal.org/project/panopoly
      Recruiter 1.1.2 -------------- https://drupal.org/project/recruiter
      Spark 1.0-b1 ----------------- https://drupal.org/project/spark
      Totem 1.1.2 ------------------ https://drupal.org/project/totem
      Ubercart 3.6 ----------------- https://drupal.org/project/ubercart
    
      ### Pressflow 6.30.1
    
      Commons 2.16 ----------------- https://drupal.org/project/commons
      Feature Server 1.2 ----------- http://bit.ly/fserver
      Managing News 1.2.4 ---------- https://drupal.org/project/managingnews
      Open Atrium 1.7.2 ------------ https://drupal.org/project/openatrium
      Pressflow 6.30.1 ------------- http://pressflow.org
      Ubercart 2.13 ---------------- https://drupal.org/project/ubercart
    
    # New features and enhancements in this release:
    
      * Add High-performance JavaScript callback handler (js) in all platforms.
      * Add session_expire module to shared contrib space in all platforms.
      * Add support for session.cookie_lifetime configurable via INI variable.
      * Allow to control swap clear with control file /root/.no.swap.clear.cnf
      * Auto-Update all BOA install and upgrade wrappers daily.
      * Default system /bin/sh symlink target replaced with /bin/websh wrapper.
      * Disable tcp_slow_start_after_idle for better SPDY performance.
      * Improve the logic in the global.inc for faster processing.
      * Issue #1217486 - Add o_contrib symlinks on platform Verify task.
      * Issue #1310054 - Add support for drush aliases in all lshell accounts.
      * Issue #2148335 - Add Default Localhost Vhost.
      * Issue #2166641 - Make hard-coded load thresholds configurable.
      * Issue #2170079 - Use _CUSTOM_CONFIG_LSHELL to protect lshell.conf template.
      * Issue #2226919 - Custom Platforms in Version Control (skip permissions fix).
      * Lshell: Update /etc/lshell.conf only when required instead of every 5 min.
      * Manage extra db GRANT for 127.0.0.1 to allow SSH tunneling for SQL access.
      * New option _REDIS_LISTEN_MODE to configure PORT or SOCKET mode globally.
      * Nginx: Add support for protected PHP-FPM monitor.
      * Nginx: Force aggressive no-cache headers for the under construction page.
      * Nginx: Switch to buffered logging when /root/.high_traffic.cnf exists.
      * PHP: Add support for FPM/CLI version safe switch per Octopus instance.
      * PHP: Allow to install and run all supported versions: 5.5, 5.4, 5.3, 5.2
      * PHP: Extra php.ini files automatically managed per system and shell user.
      * PHP: FPM workers in 5.5, 5.4 and 5.3 will use 'ondemand' mode by default.
      * PHP: Use separate FPM pools per Octopus instance.
      * PHP: Use TCP Socket mode for all FPM pools and Port mode for legacy vhosts.
      * Protect ~/.drush and other important directories and symlinks from changes.
      * Redis: Allow to exclude cache bins on the fly, per site or per platform.
      * Save 295 seconds on BOA Install and Upgrade.
      * Set and auto-manage strict permissions on some important config files.
      * Set PHP CLI version in the /bin/websh wrapper on the fly.
      * Use Two-Factor-like Authentication logic for Chive DB Manager access.
      * Improve `sqlmagic fix file.sql` to properly replace INSERT INTO with
        INSERT IGNORE INTO (a workaround for duplicate keys in the DB dump)
      * Use the same trick with modules/local-allow.info to temporarily make
        civicrm.settings.php writable, if exists.
    
    # Changes in this release:
    
      * Add ~/static/trash/* to automatic daily cleanup.
      * Add coder to auto-disabled modules -- see #2068771
      * Allow 'drush uli' as root, but deny root access to Drush by default.
      * Disable D8 install via _ALLOW_UNSUPPORTED until next release.
      * Do not enable SYNFLOOD protection by default.
      * Do not force old_short_name in any profile file directly.
      * Firewall: Allow to connect to Apple Push Notification service (APNs)
      * Issue #289 - Update lshell env_path for RVM and install/update global gems.
      * Issue #292 - Open standard RTMP port 1935.
      * Lshell: Use latest Drush 6 (master) by default and remove other versions.
      * Nginx and PHP-FPM: Better default timeout limits.
      * Nginx: Add apk, pxl, ipa to known mime types / download extensions.
      * Nginx: Use text/xml mime type for .xml URLs and restore other mime defaults.
      * Open local access for web based sites cron.
      * Open outgoing port 2525 for custom SMTP connections.
      * Percona DB server is no longer supported.
      * PHP: Always build from sources.
      * PHP: Disable 5.2 FPM if installed, but not used.
      * PHP: Only critical errors are enabled by default in the CLI mode.
      * PHP: Reloading FPM hourly no longer makes any sense.
      * PHP: Remove support for deprecated APC and Memcached.
      * PHP: Restore MailParse support - 2.1.6
      * PHP: Use aggressive disable_functions defaults (further tuned per FPM pool).
      * Redis: Integration module (the modern variant) upgrade to 7.x-2.x-o8-2.6-A
      * Redis: Use modern version with enabled fast lock and aggressive flush mode.
      * Remove insecure exception for wkhtmltopdf uploaded in the user space.
      * Rename master repository on GitHub from legacy nginx-for-drupal to boa.
      * Set _STRICT_BIN_PERMISSIONS=YES by default.
      * Upgrade Compass Tools on every upgrade, not just on new BOA release.
      * Use 60s opcache.revalidate_freq by default to save disk I/O on live sites.
      * Use Ruby Version Manager (RVM) by default to manage Compass Tools etc.
      * Use RVM for global gem installation and updates.
      * Use search_api_solr-7.x-1.4 for new installs.
      * Use web based cron by default to benefit from Zend OPcache.
      * Do not check existence nor auto-config Purge/Expire unless INI variable
        purge_expire_auto_configuration is set to TRUE (automatically, when
        the module is detected as enabled).
      * New naming convention for Ubercart 3.x platforms: [ud2] to support upgrades
        from uberdrupal profile, and [aq3] to support upgrades from acquia profile.
        Note that you have to choose Vanilla Testing profile to see [ud2] or
        Vanilla Minimal to see [aq3] platform in the Add Site form.
      * GitHub is now our main repository, we re-open the issue queue there
        for patches merge requests, while d.o has a code mirror status from now on.
      * Make it crystal clear that Ubuntu is barely supported, rarely tested and
        thus not recommended.
      * The "Run cron" extra task has been removed for security reasons. Site cron
        can be run either via standard, scheduled in Aegir procedure, which uses
        local, but web based request to the protected /cron.php URL, or on command
        line, or from the site admin area, as usual.
    
    # System upgrades in this release:
    
      * Bazaar Version Control System (bzr) 2.6.0
      * Collectd Graph Panel (CGP) master-30-03-2014
      * cURL 7.36.0 (if installed from sources)
      * Git 1.9.1 (if installed from sources)
      * Jetty 7.6.14, 8.1.14, 9.1.3
      * Limited Shell 0.9.16.5-om8
      * MariaDB 5.5.36
      * MySecureShell 1.32
      * Nginx 1.5.12
      * OpenSSH 6.6p1 (if installed from sources)
      * OpenSSL 1.0.1f (if installed from sources)
      * PHP 5.4.26
      * PHP 5.5.10
      * PHP: Imagick 3.1.2
      * PHP: ionCube loader 4.5.3
      * PHP: MongoDB 1.4.5 (optional add-on)
      * PHP: Zend OPcache master-09-03-2014
      * PHPRedis: master-22-03-2014
      * Redis 2.8.8
      * Ruby 2.1.1 (from now on compiled from sources)
    
    # Fixes in this release:
    
      * Add fix_collectd_nginx for Collectd config update.
      * Add missing panopoly_demo app in the Panopoly distro to fix broken install.
      * Add missing variables to active INI files, if needed.
      * Avoid way too long Speed Booster TTL for bots, especially for rss feeds.
      * Changing old_short_name mapping to: uberdrupal->testing and acquia->minimal
      * Do not force old_short_name if already set in db/drushrc.
      * Do not run swap clean when heavy tasks like cdp backup run.
      * Drush: Simplify and improve access restrictions logic when aliases are used.
      * Excessive and useless Drush internal cache clear in daily.sh removed.
      * Fix default PATH in all sub-scripts.
      * Fix for broken cURL from sources install logic.
      * Fix for drush make broken by websh fix for cd wildcard crash fix.
      * Fix for multi-IP cron access.
      * Fix missing /dev/fd early enough to avoid broken tasks in Aegir.
      * Fix the logic in manage_ip_auth_access()
      * Fix to avoid daily services maintenance/cron freeze if Jetty didn't stop.
      * Force backward compatible SERVER_SOFTWARE to silence core warnings.
      * Force OpenSSH rebuild on OpenSSL upgrade (if installed from sources).
      * Issue #1317322 - Filters UI broken.
      * Issue #1991908 - Fix the syslog flood caused by collectd df plugin.
      * Issue #2057213 - Use better SQL GRANT style.
      * Issue #2110589 - Unable to install BOA correctly on Debian 6.0 and OpenVZ
      * Issue #2141283 - Drush aliases like `drush dbup` no longer work properly.
      * Issue #2144801 - Display bug on add site.
      * Issue #2144947 - Install new Ruby for better compatibility with new gems.
      * Issue #2150557 - Make the check and update procedure for UseDNS safe.
      * Issue #2152383 - Fix for [js module] - add js_server_software variable.
      * Issue #2159881 - Drush is broken because Console_Table URL no longer works.
      * Issue #2161115 - AdvAgg: Strictly follow RFC 2616 14.21
      * Issue #2167141 - Do not exclude --with-ldap --with-gmp in the PHP on Wheezy.
      * Issue #2172089 - Fix for syntax error.
      * Issue #2173209 - Do not use legacy (removed) symlink for version check.
      * Issue #2175197 - Regex configuration not matching esi/ssi tags.
      * Issue #2177837 - process.max not set correctly for PHP 5.5 and 5.4
      * Issue #2182671 - Solr 4 with Jetty 8 does not start after upgrade.
      * Issue #2188907 - Update docs criteria for not rebuilding ssh, ssl, and curl.
      * Issue #2199229 - CiviCRM 4.4.4 Requires change in the Nginx configuration.
      * Issue #288 - SMTP Authentication Module depends on fsockopen.
      * Lshell: Fix for crash on wildcard cd.
      * Lshell: Remove symlinks for legacy drush_make.
      * Modules can be incorrectly whitelisted from dis by installation profile.
      * Nginx: Add exceptions for known video players.
      * Nginx: Avoid downtime on upgrade because of too low variables_hash_max_size
      * Nginx: Better gzip defaults.
      * Nginx: Default value of variables_hash_max_size is too low.
      * Nginx: Do not overwrite gzip_types.
      * Nginx: Improve fastcgi defaults.
      * Nginx: Remove too broad regex for 'flag' keyword in the URI.
      * Nginx: Send Access-Control-Allow-Origin * header also for /favicon.ico
      * Nginx: Use port 9090 in nginx_octopus_include.conf by default (PHP-FPM 5.3)
      * Nginx: Use Redirect 301 for legacy paths /sites/drupal/files/*
      * Once you have next 2.3.x installed, you can't downgrade to legacy 2.2.x
      * PHP: Add protection for instance level php.ini files.
      * PHP: Fix for broken build when --with-ldap is used.
      * PHP: Fix for broken dependencies in newer Debian and Ubuntu systems.
      * PHP: Fix for forced rebuild mode if lib curl is broken or updated with apt.
      * PHP: Fix for GEOS 3.4.2 and multi-version install.
      * PHP: Fix for legacy 5.2 logic.
      * PHP: Force 5.5 to use correct SQL drivers so its built-in will not be used.
      * PHP: Reduce duplicate rebuilds.
      * PHP: The --with-curlwrappers option has been removed in 5.5
      * Redis: Auto-Restart if socket is missing only when socket mode is enabled.
      * Redis: Exclude cache_form bin or it will break modules like ajax_comments.
      * Redis: Force clean restart daily, with long enough sleep time.
      * Redis: Restore pwd protection.
      * Redis: The cache_metatag bin needs aggressive flush mode -- see #2062379
      * Reduce system load during db backups with short delays between databases.
      * Remove collectd on major system upgrade even if /var/www/cgp doesn't exist.
      * Silence AIS (Adaptive Image Styles) module .htaccess requirements.
      * Sort and group cnf variables to bring some order into this chaos.
      * Symlink main drush wrapper to shared location outside of Master Instance.
      * Update for Redis bins exceptions logic.
      * Update system load check method in all scripts.
      * Use forced Jetty restart mode.
      * Use https in the welcome screen image src URL.
      * Use IPv4-strict hostname and IP checks only.
    
    
    # Known Issues on systems upgraded to BOA-2.2.0 release (all fixed)
    
      ==> Updated on Tue Apr  1 12:20:27 SGT 2014
    
      @=> Issues hot-fixed in stable (run 'barracuda up-stable system' to apply):
    
      * Compass Tools don't use correct paths to Ruby 2.1.1
      * Chive Authentication via SSH session doesn't work on some older instances.
      * PHP: Disabled 'create_function' may break some contrib modules or code.
      * PHP: Disabled 'assert' may cause warnings on features revert.
      * Cron for sites doesn't work on old instances without Nginx wildcard vhost.
      * The 'git pull' command is broken in limited shell.
      * FTPS (FTP over SSL) connections may experience TLS problems.
      * The 'rsync' command is broken in limited shell.
      * The drush dl foo can't be run outside of site directory.
    


 You can read the full changelog as always at: http://bit.ly/newboa

Enjoy!