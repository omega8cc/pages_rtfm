---
title: BOA-2.0.9 Barracuda Edition
slug: boa-209-barracuda-edition-257
menu: BOA-2.0.9 Barracuda Edition
date: 09-05-2013
published: true
publish_date: 09-05-2013
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

We are happy to release BOA-2.0.9 Barracuda Edition, which includes security upgrades, many fixes and improvements introduced in the last 30 days since previous Edition. This is the first Barracuda-only Edition, released to address important security issue with Nginx server and provide system level upgrades.

This Edition will not upgrade Aegir Master nor Aegir Satellite Instances, because there was no new Drupal core released since BOA-2.0.8 Edition and there were not enough updates to built-in platforms or contrib accumulated.

We recommend that you use system-only upgrade mode: `barracuda up-stable system` after starting `screen` session and wait until it will complete the upgrade and will send you a report via e-mail.

Releasing Barracuda-only Edition separately from full Edition allows us to address system/services security issues without any extra delay, while releasing Octopus-only Edition will allow us to provide Drupal core or Aegir version upgrades, without affecting system level services.

There is also another reason why separate releases will be useful. BOA-2.0.9 is the last Edition where Aegir 2.x uses still old Drush 4.6 in the backend. We need to sync BOA specific Aegir 2.x with upstream and finally switch to Drush 5, or even Drush 6, if possible.

This change, however, may cause issues if you still host legacy Drupal 5 or some old Drupal 6 sites, with either core or contrib not compatible with PHP 5.3, which is now used by default.

That is why we plan to introduce ability to install older/previous Barracuda and/or Octopus release, if you need more time to upgrade.

 
    ### Stable BOA-2.0.9 Release - Barracuda Edition
    ### Date: Thu May  9 11:25:59 EDT 2013
    ### Includes Aegir from BOA-2.0.8 Edition
    
    # New features and enhancements in this release:
    
      * Debian 7.0 Wheezy support.
      * Automated upgrade from Squeeze with _SQUEEZE_TO_WHEEZY=YES option.
      * Added config template with inline how-to in docs/cnf/barracuda.cnf
      * Added config template with inline how-to in docs/cnf/octopus.cnf
      * Added passwords encryption how-to in docs/BLOWFISH.txt
      * Added the list of symbols used on install in docs/PLATFORMS.txt
      * Forced mysql restart if there are too many high CPU mysqld processes.
      * Improved docs/NOTES.txt
      * Improved docs/README.txt
      * Install libpam-unix2 and libxcrypt1 by default.
      * Install s3cmd by default.
      * Issue #1974640 - Allow to use Midnight Commander for limited shell users.
      * Limited Shell Logs Monitor enabled by default.
      * Nginx: Check for Linux/Cdorked.A malware and delete if discovered.
      * Re-generate and sync Aegir passwords before and after instance upgrade.
      * The silent 'system' mode documented in docs/UPGRADE.txt
      * Allow to exclude platform from otherwise forced `drush en entitycache -y`
        if sites/all/modules/entitycache_dont_enable.info control file is present.
    
    # Changes in this release:
    
      * Nginx 1.5.0 - security upgrade for CVE-2013-2028
      * PHP 5.3.25
      * Redis 2.6.13
      * Do not disable update module in platforms known to include it as required.
      * Firewall: Open port 1129 for outgoing connections (some gateways need it).
      * Force syslog module as disabled by default and save some disk I/O.
      * Tune kernel to always use max RAM and not swap, if possible.
    
    # Fixes in this release:
    
      * Add outgoing port 25 SMTP to the list of requirements.
      * Firewall: Add truly permanent block for heavy abusers.
      * Fix for mytop support, available again on systems with MariaDB.
      * Fix permissions in the /data/all tree if required.
      * Fix the order of checks - they scan only the last (current) minute.
      * Force _STRONG_PASSWORDS=NO if locales still look broken on second check.
      * Improve detecting no longer running drush.php and/or cron PHP processes.
      * Improve fix_locales logic.
      * Improve global.inc symlinking on initial install and upgrade.
      * Improve messages displayed when fix_locales discovers broken locales.
      * Improve monitoring to avoid duplicate entries on low traffic systems.
      * Improve sanitize_string() filtering to avoid issues with strong passwords.
      * Improve syncpass tool - Update system user passwd and flush privileges.
      * Issue #1961226 - Warning: Could not change permissions of sites/all to 751.
      * Issue #1962458 - 403 for anonymous users on node/add.
      * Issue #1963044 - Force UTF-8 locales if not present/configured properly.
      * Issue #1974542 - Use /root/.home.no.wildcard.chmod.cnf control file.
      * Issue #1987936 - Restore ability to install PHP 5.2 for FPM and CLI.
      * Make sure that /dev/null is writable for everyone.
      * Make sure that all drushrc.php files are owned by Aegir system user.
      * Make sure that all expected sites/all/{modules,themes,libraries} dirs exist.
      * Make sure that DB server is restarted on upgrade after config tuning.
      * Make sure that pdnsd and resolvconf are properly installed.
      * Nginx: Remove duplicate Vary: Accept-Encoding headers.
      * Percona no longer supports older Ubuntu non-LTS releases.
      * PHP: Do not reload FPM every hour - it may cause error 502.
      * PHP: Fix paths depending on CLI version used.
      * PHP: Fix the extensions installation and upgrade logic.
      * PHP: Make sure that the FPM port is set correctly for D6 sites with 5.2
      * PHP: Properly uninstall all related packages when using source build.
      * PHP: Start more FPM workers on systems with enough RAM by default.
      * Purge bin logs before disabling them.
      * Run NewRelic re-install early enough to avoid locking full-upgrade.
      * Sync the load limits for spiders and backend tasks.
      * The Java/Jetty monitor should use higher allowed limits by default.
      * Update apticron message to recommend system mode instead of full upgrade.
      * Update docs for _BUILD_FROM_SRC option.
      * Use aggressive enough Jetty restart procedure on nightly services reload.
      * Use correct status messages on install and upgrade.
      * Use installer and not Aegir version download on stable install/upgrade.


 You can read full changelog as always at: http://bit.ly/newboa

Enjoy!