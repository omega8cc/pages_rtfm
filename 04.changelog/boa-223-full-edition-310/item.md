---
# http://learn.getgrav.org/content/headers
title: BOA-2.2.3 Full Edition
slug: boa-223-full-edition-310
# menu: BOA-2.2.3 Full Edition
date: 18-04-2014
published: true
publish_date: 18-04-2014
# unpublish_date: 18-04-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

 We are happy to release BOA-2.2.3 Full Edition, which includes several bug fixes and security upgrades both for the system services and Drupal core, along with three updated platforms and a few new features.

 
    ### Stable BOA-2.2.3 Release - Full Edition
    ### Date: Fri Apr 18 12:57:40 PDT 2014
    ### Includes Aegir 2.x-boa-custom version.
    
    # Release Notes:
    
      This release includes several bug fixes and security upgrades both for the
      system services and Drupal core, along with three updated platforms and new
      features, including support for MariaDB 10.0 and Ubuntu 14.04 LTS Trusty.
    
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
    
    # Updated Octopus platforms:
    
      ### Drupal 7.27.1
    
      Guardr 1.3 ------------------- https://drupal.org/project/guardr
      Open Atrium 2.17 ------------- https://drupal.org/project/openatrium
      Recruiter 1.2 ---------------- https://drupal.org/project/recruiter
    
    # New features and enhancements in this release:
    
      * Add docs/FAQ.txt
      * Add support for MariaDB 10.0 or 5.5 install via _DB_SERIES variable.
      * Add support for Ubuntu 14.04 LTS Trusty.
      * Improve auto-healing for multi-version PHP-FPM setup.
      * Improve docs/UPGRADE.txt
      * Improve health check for protected vhosts during live SSH-auth update.
      * Nginx: More aggressive limits against spambots trying to register accounts.
    
    # Changes in this release:
    
      * Issue #GH-299 - Force disable LESS developer mode on production sites.
      * Move custom scripts to /opt/local/bin/
      * Nginx: Use higher defaults for limit_conn to avoid error 503 (CloudFlare)
      * Normalize localhost entry in /etc/hosts to avoid FQDN mapped to 127.0.0.1
      * PHP: Do not use separate FPM pool for cron if _PHP_FPM_DENY is empty.
    
    # System upgrades in this release:
    
      * MariaDB 5.5.37
    
    # Fixes in this release:
    
      * Add 'exit 0' line if missing.
      * Add /opt/local/bin to PATH by default.
      * Add symlinks for wrappers only temporarily.
      * Add warning that Compass Tools install and upgrade may take a LONG time.
      * Better gem uninstall options.
      * Compass: Multiple fixes for various expected gems versions install/upgrades.
      * Do not override lshell env_path in websh wrapper.
      * Do not use monitored bin path for custom scripts to avoid LFD false alarms.
      * Extra db GRANT for 127.0.0.1 not added when migrating site.
      * Improve auto-healing to create required directories in /var/run/ if missing.
      * Issue #2230269 - New Jetty 9 version overrides JETTY_PORT=8099 with 8080.
      * Issue #2235991 - Drush make needs better exceptions in websh wrapper.
      * Issue #2236475 - Clarify what the Legacy mode really means.
      * Issue #2238965 - Add missing path to switch_to_bash().
      * Issue #2241013 - Git commands should be whitelisted in websh wrapper.
      * Issue #2241495 - wkhtmltopdf stopped working after upgrade.
      * Issue #GH-301 - Update the list of restricted keywords for Octopus username.
      * Make sure that permissions on Chive Manager dir/files are correct.
      * Note: _SSL_FROM_SOURCES=YES is ignored and not needed on Wheezy and Precise.
      * PHP: Add /opt/local/bin/php tmp symlink on barracuda/octopus upgrade.
      * PHP: Allow to set custom _PHP_FPM_TIMEOUT but not lower than 60 (in seconds)
      * PHP: Always respect _PHP_FPM_WORKERS variable if set to numeric value > 0
      * PHP: pm.max_children was not properly updated on FPM version self-switch.
      * PHP: Variable _PROCESS_MAX_FPM is not used on the Satellite Instance level.
      * Remove the line with header TABLE_NAME (sqlmagic).
      * Reset PATH to avoid RVM overrides after Compass Tools install/upgrade.
      * Shell: Allow to run 'drush cache-clear drush' in any directory.
      * The _PHP_MODERN_ONLY variable is no longer used.
      * Ubuntu 14.04 LTS Trusty requires MariaDB 10.0
      * Use hostname -b instead of deprecated hostname -v.
    


 You can read the full changelog as always at: http://bit.ly/newboa

Enjoy!