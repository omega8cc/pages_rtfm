---
# http://learn.getgrav.org/content/headers
title: BOA-2.4.4 Full Edition
slug: boa-244-full-edition-364
# menu: BOA-2.4.4 Full Edition
date: 03-07-2015
published: true
publish_date: 03-07-2015
# unpublish_date: 03-07-2015
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

 We are happy to release BOA-2.4.4 Full Edition, which includes latest Drupal core plus several important system upgrades and bug fixes. Enjoy!

 
    ### Stable BOA-2.4.4 Release - Full Edition
    ### Date: Fri Jul  3 12:08:29 PDT 2015
    ### Milestone URL: https://github.com/omega8cc/boa/milestones/2.4.4
    ### Latest hotfix added on: Sat Jul  4 07:14:29 PDT 2015
    
      @=> Includes Aegir Hostmaster 2.x-head with improvements
      @=> Includes Aegir Provision 3.x-head with improvements
      @=> Includes Drush 7 customized for BOA
    
    # Release Notes:
    
      This BOA release includes several important system upgrades and bug fixes.
    
      All supported Aegir platforms have been updated with latest Drupal cores.
    
      This version automatically switches all hosted sites to PHP 5.5 on systems
      hosted and managed remotely by Omega8.cc support team, unless you have
      explicitly switched your Octopus instance to use PHP version you prefer.
      Using PHP older than 5.5 is strongly discouraged, for security, stability and
      performance reasons.
    
    # Changes:
    
      * Do not change mysql root password by default -- workaround for #642
      * Enable advagg_async_generation by default
      * Redis Integration Module: Update to version mod-26-06-2015
      * Use modern ssl_ciphers in all templates by default
    
    # System upgrades:
    
      * cURL 7.43.0 (if installed from sources)
      * Drush mini-7-30-06-2015 -- fixes #734
      * MariaDB 5.5.44
      * MariaDB Galera Cluster 10.0.20
      * Nginx 1.9.1
      * OpenSSH 6.9p1 (if installed from sources)
      * OpenSSL 1.0.1o (if installed from sources)
      * PHP 5.4.42
      * PHP 5.5.26
      * PHP 5.6.10
      * PHPRedis master-27-06-2015
      * Pure-FTPd 1.0.41
      * vnStat 1.14
    
    # Fixes:
    
      * Add 'grep' to overssh -- a list of commands allowed to execute over SSH
      * Broken pdnsd configuration breaks DNS resolver -- fixes #701
      * Do not modify rkey/debug args in barracuda log/system upgrade mode
      * Don't remove Drupal 6 core themes -- fixes #738
      * Fix for legacy vnStat config
      * Fixed backboa/duobackboa retrieve from remote host -- fixes #741
      * Improve system cron tasks queue
      * Incorrect permissions on /usr/bin/optipng - fixes #722
      * Mitigate LOGJAM - fixes #723
      * Restart Postfix after system DNS update -- #701
      * Skip daily reload on high traffic instances
      * Sync SQL connection limits with _PHP_FPM_WORKERS variable - fixes #699
      * Use _AWS_URL to properly handle us-east-1 exception
      * Use 2048 bit where possible - see #723
      * Use better default value for advagg_cache_level - fixes #726


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!