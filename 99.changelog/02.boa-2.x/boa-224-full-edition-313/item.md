---
# http://learn.getgrav.org/content/headers
title: BOA-2.2.4 Full Edition
slug: boa-224-full-edition-313
# menu: BOA-2.2.4 Full Edition
date: 30-04-2014
published: true
publish_date: 30-04-2014
# unpublish_date: 30-04-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.2.4 Full Edition, which includes several bug fixes and security upgrades both for the system services and Drupal core, along with five updated platforms and some new features.

 
    ### Stable BOA-2.2.4 Release - Full Edition
    ### Date: Wed Apr 30 17:03:36 PDT 2014
    ### Includes Aegir 2.x-boa-custom version.
    ### Latest hotfix added on: Fri May  2 04:54:25 PDT 2014
    
    # Release Notes:
    
      This release includes several bug fixes along with five updated platforms,
      plus some hot-fixes applied to previous stable after its release. We have
      also added a fix for known problem is recent Drupal 7.27 [#2245331] hence
      the change from Drupal 7.27.1 to 7.27.2 in all D7 platforms.
    
    # Important - Read This First! (for self-hosted BOA only)
    
      If you haven't run full barracuda+octopus upgrade to latest BOA Stable
      Edition yet, don't use any partial upgrade modes explained in docs/UPGRADE.txt
      Once new BOA Stable is released, you must run *full* upgrades with commands:
    
      $ barracuda up-stable
      $ octopus up-stable all both
    
      For silent, logged mode with e-mail message sent once the upgrade is
      complete, but no progress is displayed in the terminal window, you can run
      alternatively, starting with screen session to avoid incomplete upgrade
      if your SSH session will be closed for any reason before the upgrade
      will complete:
    
      $ screen
      $ barracuda up-stable log
      $ octopus up-stable all both log
    
      Note that the silent, non-interactive mode will automatically say Y/Yes
      to all prompts and is thus useful to run auto-upgrades scheduled in cron.
    
      If you have skipped some recent BOA releases, and you have new default config
      option: _PERMISSIONS_FIX=NO in your /root/.barracuda.cnf configuration file,
      plus, you are not sure if you follow best practices for managing permissions
      as recommended in our docs: https://omega8.cc/node/116 then we recommend
      that you change it to _PERMISSIONS_FIX=YES temporarily, or even permanently
      if your VPS is fast enough, and then run this powerful script as root:
    
      $ bash /var/xdrago/daily.sh
    
      Note that BOA 'legacy' mode is still at version 2.1.3
    
    # Updated Octopus platforms:
    
      ### Drupal 7.27.2
    
      Commerce 1.25 ---------------- https://drupal.org/project/commerce_kickstart
      Commerce 2.14 ---------------- https://drupal.org/project/commerce_kickstart
      Commons 3.11 ----------------- https://drupal.org/project/commons
      Panopoly 1.5 ----------------- https://drupal.org/project/panopoly
    
      ### Pressflow 6.31.1
    
      Commons 2.17 ----------------- https://drupal.org/project/commons
    
      Note: Always read and follow upgrade procedure if explained in the distro
      release notes, like for Panopoly 1.5 at https://drupal.org/node/2255133
    
    # New o_contrib modules:
    
      * print-6.x-1.19 (includes patch to auto-detect /usr/bin/wkhtmltopdf)
      * print-7.x-2.0  (includes patch to auto-detect /usr/bin/wkhtmltopdf)
    
    # New features and enhancements in this release:
    
      * Support for session.gc_maxlifetime configurable via INI files.
    
      You can control session garbage collector (EOL) per site and per platform.
      The value (in seconds) of the session_gc_eol variable is used as
      session.gc_maxlifetime value and specifies the number of seconds after which
      data will be seen as 'garbage' and potentially cleaned up, resulting with
      $_SESSION variable discarded and affected authenticated users logged out.
    
      BOA default defined in the system level global.inc file is 86400 == 24h.
    
    # Changes in this release:
    
      * Drush: Upgrade command line version 6 to mini-6-26-04-2014
      * Nginx: Use higher defaults for limit_conn to avoid error 503 (CloudFlare)
      * Nginx: Use more aggressive limits against spambots trying to rgstr accounts.
      * Redis: Integration module (the modern variant) upgrade to 7.x-2.x-o8-2.6-B
    
    # System upgrades in this release:
    
      * Nginx 1.7.0
      * PHP 5.5.12
      * Redis 2.8.9
    
    # Fixes in this release:
    
      * Add symlinks in the home directory if missing (every 5 minutes).
      * Add warning that Compass Tools install and upgrade may take a LONG time.
      * Always define _PHP_CN variable properly.
      * Do not delete symlinks to wrappers to avoid false LFD alarms.
      * Fix for 'Force backward compatible SERVER_SOFTWARE'.
      * Fix in websh for _IN_PATH logic to not break backend Drush tasks.
      * Fix the logic for wrappers update and symlinks.
      * Improve status messages to display when silent mode is used on upgrade.
      * Improve whitelisting in the websh wrapper.
      * Issue #2238805 - Command filtering - no word containing *drush* is allowed.
      * Issue #2241495 - wkhtmltopdf stopped working after upgrade.
      * Issue #2247997 - Update docs/REMOTE.txt with workaround for websh issue.
      * Issue #2250397 - Always follow (limited) redirects in cURL requests.
      * Issue #GH-304  - [rvm] use $_RUBY_VERSION as default.
      * Issue #GH-305  - Check disk usage before running install/upgrade.
      * Issue #GH-306  - Allow ruby 1.8 to remain installed.
      * Nginx: Allow to configure keywords for aggressive requests rate monitoring.
      * Nginx: Do not overwrite custom symlinks to the Under Construction template.
      * Nginx: Sync FastCGI timeouts with other Nginx and PHP-FPM defaults.
      * PHP: Add /opt/local/bin/php tmp symlink on barracuda/octopus upgrade.
      * PHP: Allow to set custom _PHP_FPM_TIMEOUT but not lower than 60 (in seconds)
      * PHP: Always respect _PHP_FPM_WORKERS variable if set to numeric value > 0
      * PHP: Better defaults for realpath_cache_ttl and realpath_cache_size.
      * PHP: Fix for CVE-2014-0185 privilege escalation in FPM (doesn't affect BOA)
      * PHP: pm.max_children was not properly updated on FPM version self-switch.
      * PHP: Sync incorrect default_socket_timeout with max_execution_time (180s).
      * PHP: Use 30s for pm.process_idle_timeout - it prevents too high RAM usage.
      * PHP: Variable _PROCESS_MAX_FPM is not used on the Satellite Instance level.
      * Postfix: Force re-install if broken permisions detected on upgrade.
      * Prevent duplicate cron invocations with more strict delays.
      * Restart rsyslog once the install or upgrade is complete.
      * Set the TERM env variable if missing to avoid errors.
      * Shell: Proper fix for wildcard in the path (cd command only)
      * Standardize install and upgrade for Chive, SQL Buddy and CGP.
      * Sync Redis timeout with default FPM timeout (180s).
      * Sync SQL connect_timeout with default mysql.connect_timeout in PHP (60s).
      * The ~/static/control must be writeable by lshell user to manage ctrl files.
      * Update the logic for multi-version PHP support in BOND.
      * Update the logic for multi-version PHP support in docs/REMOTE.txt
    


 You can read the full changelog as always at: http://bit.ly/newboa

Enjoy!