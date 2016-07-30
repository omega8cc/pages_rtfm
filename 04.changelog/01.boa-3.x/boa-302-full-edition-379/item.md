---
# http://learn.getgrav.org/content/headers
title: BOA-3.0.2 Full Edition
slug: boa-302-full-edition-379
# menu: BOA-3.0.2 Full Edition
date: 03-05-2016
published: true
publish_date: 03-05-2016
# unpublish_date: 03-05-2016
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

We are happy to release BOA-3.0.2 Full Edition, which includes support for PHP 7.0.6 and compatible Drupal 7 core, along with many important fixes and improvements. Enjoy!

 
    ### Stable BOA-3.0.2 Release - Full Edition
    ### Date: Tue May  3 22:26:09 PDT 2016
    ### Milestone URL: https://github.com/omega8cc/boa/milestones/3.0.2
    ### Latest hotfix added on: Fri May  6 08:42:13 PDT 2016
    
      @=> Includes Aegir Hostmaster 3.x-head with improvements
      @=> Includes Aegir Provision 3.x-head with improvements
      @=> Includes Drush 8 customized for BOA
    
    # Release Notes:
    
      This BOA release includes several important system upgrades, improvements
      and bug fixes. All supported platforms have been updated to latest versions.
    
      @=> Latest Drupal 7 core version used in BOA in all built-in platforms is
          compatible with latest PHP 7.0.6 -- you can switch your Octopus instance
          easily via fpm.info control file: https://omega8.cc/node/330 but please
          don't use 7.0 in cli.info, because it is not supported in the Aegir
          backend yet. PHP 7.0 can't be used if you have any Pressflow 6 site.
    
    # New features and enhancements:
    
      * Add idna_convert to hostmaster for IDN domain names auto-conversion -- #916
      * Allow to disable redis.path.inc feature via INI variable -- #815
      * Drupal 7.43.2 (with PHP 7 compatibility patch)
      * PHP 7 compatibility improvements -- #716
      * Pressflow 6.38.2 (only version update)
      * Truncate giant watchdog tables
    
    # Changes:
    
      * Disable (temporarily) support for outdated ERPAL distro
      * Disable auto-upgrade for legacy Octopus instances
      * Disable page cache only in hostmaster
      * Disable PAMAuthentication in pure-ftpd
      * Force PHP 5.6 or 5.5 cli.info in Octopus 2.4.9
      * Force Redis SOCKET mode if PORT was used before
      * Redis module mod-03-05-2016
      * Redis: Limit methods to define site prefix
      * Redis: Use maxmemory-policy volatile-ttl
      * Set redis_client_base
      * Use Redis in hostmaster
      * Use standard profile by default
    
    # System upgrades:
    
      * Drush micro-8-24-04-2016
      * MariaDB 10.0.25
      * MariaDB 5.5.49
      * MariaDB Galera Cluster 10.0.25
      * Nginx 1.9.15
      * OpenSSL 1.0.2h (used only in custom built Nginx)
      * PHP 5.5.35
      * PHP 5.6.21
      * PHP 7.0.6
    
    # Fixes:
    
      * Add check_boa_php_compatibility() procedure -- fixes #906
      * Add patch for registration error (Commons)
      * Avoid duplicate entries in hosting_cron on hostmaster install -- #928
      * Cron not running on cloned sites -- fixes #922
      * Disable hosting-pause / Provision -- not needed in BOA, may hang upgrade
      * Do not force TERM
      * Do not set $conf['redis_eval_enabled'] = TRUE;
      * Enable _DEBUG_MODE=YES on Octopus upgrade from BOA-2.4.9
      * Experimental hosting_git error, platform not installed -- fixes #904
      * Improve the provision_autoload_register_prefix check
      * Make sure that auto-generated robots.txt is OK -- fixes #925
      * Make sure that hostmaster cron is never disabled
      * Make sure to not set PHP 7 as system default
      * Restart php-fpm on upgrade as soon as possible
      * Run registry-rebuild directly after hostmaster-migrate
      * Run update_php_cli_cron() twice
      * Use inetutils-syslogd on VZ systems -- fixes #905
      * Use syncpass during hostmaster upgrade
      * Workaround for hostmaster upgrade from 2.x


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!