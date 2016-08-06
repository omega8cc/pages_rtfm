---
# http://learn.getgrav.org/content/headers
title: BOA-2.2.5 Full Edition
slug: boa-225-full-edition-314
menu: BOA-2.2.5 Full Edition
date: 08-05-2014
published: true
publish_date: 08-05-2014
# unpublish_date: 08-05-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.2.5 Full Edition, which includes bug fixes, three updated distributions and latest Drupal 7.28.1 and Pressflow 6.31.2 core in all built-in Octopus platforms.

 
    ### Stable BOA-2.2.5 Release - Full Edition
    ### Date: Thu May  8 11:59:23 PDT 2014
    ### Includes Aegir 2.x-boa-custom version.
    ### Latest hotfix added on: Fri May  9 08:00:15 PDT 2014
    
    # Release Notes:
    
      This release includes no new features, but does include bug fixes plus latest
      Drupal 7.28.1 and Pressflow 6.31.2 core in all built-in Octopus platforms.
      There are also three updated distributions included, as listed below.
      We also list here all hot-fixes applied to previous stable after its release.
    
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
    
      Commons 3.12 ----------------- https://drupal.org/project/commons
      Open Atrium 2.18 ------------- https://drupal.org/project/openatrium
      Open Outreach 1.6 ------------ https://drupal.org/project/openoutreach
    
    # Changes in this release:
    
      * Add rsyslog/sysklogd to auto-healing procedures.
      * Make the aggressive scan_nginx mode optional and use old mode by default.
      * Nginx: Add HiScan to blocked crawlers list.
      * Nginx: Add Riddler to blocked crawlers list.
      * PHP: Use pm.process_idle_timeout = 10s for speed and RAM optimization.
    
    # System upgrades in this release:
    
      * MySecureShell 1.33
      * PHP 5.4.28
      * PHP 5.5.12
    
    # Fixes in this release:
    
      * Always define _PHP_CN variable properly.
      * Firewall: Sync CONNLIMIT for web ports with updated limit_conn in Nginx.
      * Force Pure-FTPd server re-install if key files are missing for any reason.
      * Issue #2237167 - Improve authorized IPs detection in all protected vhosts.
      * Issue #2262935 - Modules dir must be group writable in custom platforms.
      * Nginx: Do not overwrite custom symlinks to the Under Construction template.
      * Nginx: Update limit_conn in all instances and vhosts on Barracuda upgrade.
      * PHP: Delete pear in legacy paths, if still exists.
      * PHP: Fix for CVE-2014-0185 privilege escalation in FPM (doesn't affect BOA)
      * Postfix: Force re-install if broken permisions detected on upgrade.
      * Pressflow 6: Fix #GH 84 by using drupal_page_is_cacheable().
      * Pressflow 6: Merge pull request #GH 85 from pressflow/SA-CORE-2014-002-fix.
      * Pressflow 6: Remove duplicate openid_update_6001().
      * Revert "Force MariaDB 5.5 re-install".
      * Set the TERM env variable if missing to avoid errors.
      * Skip packages set on hold when running apticron.
      * The ~/static/control must be writeable by lshell user to manage ctrl files.
      * Add extra cron semaphore to prevent concurrent cron invocations via
        multiple running runner.sh instances.
    


 You can read the full changelog as always at: http://bit.ly/newboa

Enjoy!