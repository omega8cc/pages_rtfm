---
title: BOA-2.0.5 Edition
slug: boa-205-edition-239
menu: BOA-2.0.5 Edition
date: 23-12-2012
published: true
publish_date: 23-12-2012
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.0.5 Edition, which includes 12 updated platforms, new Drupal 7 and Drupal 6 core versions and many fixes and improvements introduced in the last six weeks since previous Edition.


    ### Stable Edition BOA-2.0.5
    ### Date: Sun Dec 23 15:35:46 EST 2012
    ### Installs Aegir 2.0.5 compatible with Aegir 1.9

    # Updated Octopus platforms:

      Commerce 1.12.1 -------------- http://drupalcommerce.org
      Commerce 2.0 ----------------- http://drupalcommerce.org
      Commons 2.11 ----------------- http://acquia.com/drupalcommons
      Drupal 7.18.1 ---------------- http://drupal.org/drupal-7.18
      Open Deals 1.14 -------------- http://opendealsapp.com
      Open Outreach 1.0-rc7 -------- http://openoutreach.org
      OpenChurch 1.11-beta7 -------- http://openchurchsite.com
      Panopoly 1.0-rc3 ------------- http://drupal.org/project/panopoly
      Pressflow 6.27.1 ------------- http://pressflow.org
      ProsePoint 0.45 -------------- http://prosepoint.org
      Ubercart 2.11.1 -------------- http://ubercart.org
      Ubercart 3.3.1 --------------- http://ubercart.org

      All other not listed above platforms are available with latest
      D6 or D7 core, even if there were no new distro version released.

    # New Aegir modules or extensions:

      * Add drush clean-modules command - clean_missing_modules extension.

    # New o_contrib modules:

      * Add reroute_email module in both D6 and D7 contrib.

    # Changes:

      * Git 1.8.0.2
      * MariaDB 5.3.11 on Debian Lenny
      * MariaDB 5.5.28a
      * Nginx 1.3.9
      * PHP 5.3.20
      * Redis 2.6.7
      * Delete old tmp files in all sites daily.
      * Disable Expire and Purge modules by default - they are no longer needed.
      * Redis integration module updated to 7.x-2.0-beta2
      * There is no need to restart Redis and Tomcat hourly.
      * Use higher innodb_lock_wait_timeout by default - 120 instead of 50.
      * Use 1h instead of 30min default timeout for sql and php-cli to avoid
        breaking some extra long running backend tasks on some really big sites.

    # Fixes:

      * Allow more drush commands over SSH.
      * Always force drupal_http_request_fails to FALSE to avoid false alarm.
      * Better check for standalone vhosts firewall setup.
      * Better lshell forbidden list of keywords.
      * Better regex to deny wildcards with top-level or country level domains.
      * Check for existence of host_master and not host_master/001 directory.
      * Compass is not available on older OS versions.
      * Delete ltd-shell extra user/client if there is no site associated/owned.
      * Delete old symlinks in the client directory for no longer associated sites.
      * Fix broken usage.sh script - it does not enable/disable modules.
      * Fix date formatting also in the sqlcheck script.
      * Fix for some really old installs without .barracuda.cnf file.
      * Fix permissions for Boost cache directory with correct chmod.
      * Fix the hint - it should say to restart mysql.
      * Issue #1081266 - Avoid re-scanning modules directory.
      * Issue #1263602 - Force New Relic re-install on every upgrade, if used.
      * Issue #1460882 - Send .json requests to @drupal instead of =404.
      * Issue #1837418 - Fix permissions inside ~/.drush directory.
      * Issue #1837776 - Do not disable httprl module.
      * Issue #1837910 - Upload progress broken for all D6 sites.
      * Issue #1839122 - Disabling Redis on known AJAX calls breaks UI elements.
      * Issue #1839544 - Use language neutral checks for users, groups and hosts.
      * Issue #1841230 - BOA provides Apache Solr 1.4 with Tomcat 6.
      * Issue #1841246 - Fix csf.fignore file to whitelist /tmp/drush_*
      * Issue #1842554 - Replace broken links to Skitch screenshots.
      * Issue #1847682 - Fix extra Nginx config support in the Master Instance.
      * Issue #1850034 - Disable SYSLOG_CHECK in csf to avoid false alarms.
      * Issue #1857250 - Domain Access support is broken in the backend cli.
      * Issue #1857990 - Include reroute_email module in o_contrib by default.
      * Issue #1860100 - Use provision-backup-delete instead of backup_delete.
      * Issue #1865112 - Add drush clean-modules command.
      * Issue #1867264 - Too many Redis caching exceptions cause serious confusion.
      * Issue #1871060 - CiviCRM l10n should be moved to proper directory.
      * Lshell: Map drush mup to up instead of upc. Add new drush mupc map for upc.
      * Max supported version of Search API Solr search is 7.x-1.0-rc2
      * More complete permissions fix on install and upgrade.
      * More strict check for _LENNY_TO_SQUEEZE option.
      * Nginx: Better regex in the Nginx monitor.
      * Nginx: Exclude also files/progress path in the Nginx monitor.
      * Nginx: Fix rewrite rules in the CDN Far Future expiration support.
      * Nginx: Make sure that any older packages are uninstalled on upgrade.
      * Nginx: Make sure that default Nginx vhosts are deleted also on upgrade.
      * Nginx: Skip all logged media and download requests in the Nginx monitor.
      * PHP: Use high enough value for max_input_vars in PHP 5.3 by default.
      * Really fix the datestamp comparison logic on various systems.
      * Rebuild registry without --no-cache-clear option to avoid issues.
      * Redis: Check if Redis binary exists, not symlink.
      * Redis: Delete redis-server symlink to avoid failed Redis install.
      * Redis: Do not use all three extra exceptions on the hostmaster site.
      * Redis: Do not use sleep breaks during Redis full restart.
      * Redis: The cache_menu bin should be still excluded from Redis caching.
      * Redis: The hostmaster site needs exception for cache_class_cache bin.
      * Stop and Start CSF only if installed.
      * The locked auto-healing script needs to kill tomcat more aggressively.
      * Update csf.conf template.
      * Upgrade to ctools-6.x-1.10 in the hostmaster platform.
      * Use aliases in drush commands where possible.
      * Use better name for non-web NewRelic app tracking.
      * You must remove remote_import extension from the source server.


 You can read full changelog as always at: http://bit.ly/newboa

Enjoy!
