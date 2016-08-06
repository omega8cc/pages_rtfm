---
# http://learn.getgrav.org/content/headers
title: BOA-2.4.7 Full Edition
slug: boa-247-full-edition-371
menu: BOA-2.4.7 Full Edition
date: 04-12-2015
published: true
publish_date: 04-12-2015
# unpublish_date: 04-12-2015
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.4.7 Full Edition, which includes several important system upgrades and  
 bug fixes, plus platforms with latest Drupal cores. Enjoy!

 
    ### Stable BOA-2.4.7 Release - Full Edition
    ### Date: Fri Dec  4 08:09:21 PST 2015
    ### Milestone URL: https://github.com/omega8cc/boa/milestones/2.4.7
    ### Latest hotfix added on: Mon Dec  7 15:32:44 PST 2015
    
      @=> Includes Aegir Hostmaster 2.x-head with improvements
      @=> Includes Aegir Provision 3.x-head with improvements
      @=> Includes Drush 7 customized for BOA
    
    # Release Notes:
    
      This BOA release includes several important system upgrades and bug fixes,
      with most notable features and changes listed below.
    
      @=> All supported Aegir platforms have been updated with latest Drupal cores
    
      @=> Drupal 8 support for custom platforms in the ~/static directory tree
          will be included, along with Drush 8 and PHP 7 in the *upcoming*
          BOA-3.0.0 release: https://github.com/omega8cc/boa/milestones/3.0.0
    
      @=> This BOA release (2.4.7) is the last release which still supports
          deprecated PHP versions: 5.3 and 5.4 -- You should switch to PHP 5.6
          or at least 5.5 as soon as possible, or you will not be able to upgrade
          to newer BOA versions after 2.4.7 -- https://omega8.cc/node/330
    
      @=> What are BOA plans for Drupal 6 support after February 24th, 2016?
    
          We will support Drupal/Pressflow 6 in all new releases, as long as
          available PHP versions will allow to use it (we run our own Pressflow 6
          based site on PHP 5.6 for many months with zero issues). For more details
          please check: https://github.com/omega8cc/boa/issues/824
    
      @=> SSH keys for root are required by newer OpenSSH versions used in BOA
    
          BOA installs SSH from sources by default (Debian only). This means that
          password based access for root will not work once BOA is installed or
          upgraded to current stable version. It is a result of OpenSSH changes
          in recent releases and not BOA specific change. BOA will deny the initial
          install and Barracuda will refuse to run upgrade if it detects that system
          root has no SSH keys added and only password based access is available.
          You can still modify this behaviour in /usr/etc/sshd_config but future
          OpenSSH versions may still revert such changes, so it is not recommended.
    
      @=> BOA switched from SPDY to HTTP/2 + PFS on all supported OS versions
    
    # Changes:
    
      * Allow to disable SQL monitoring with /root/.no.sql.cpu.limit.cnf -- #799
      * Disable page caching on the fly where needed
      * Disable temporarily support for broken Restaurant distro
      * Do not rebuild features and entities on cache clear
      * Document new requirement: SSH keys for root -- fixes #786 #833
      * Make ioncube_loader optional and disable by default with _PHP_IONCUBE=NO
      * Nginx SSL: enable OCSP stapling by default
      * Nginx SSL: enable OCSP stapling for existing HTTPS vhosts
      * Nginx: Add ssl_dhparam to existing vhosts, if needed
      * Nginx: HTTP/2 replaces SPDY -- fixes #624
      * PHP: Add YAML extension with LibYAML
      * Preserve customized /etc/sysctl.conf -- fixes #789
      * Run modules ON/OFF only weekly -- requires _MODULES_FIX=YES (default is NO)
      * Run most of crontab, install and upgrade tasks with low priority using
        nice and ionice -- fixes #780
    
    # System upgrades:
    
      * cURL 7.45.0 (if installed from sources)
      * GEOS 3.5.0 (requires _PHP_GEOS=YES)
      * Git 2.6.1 (if installed from sources)
      * MariaDB 10.0.22
      * MariaDB 5.5.46
      * MariaDB Galera Cluster 10.0.22
      * Nginx 1.9.7
      * OpenSSL 1.0.2e (used only in custom built Nginx)
      * PHP 5.5.30
      * PHP 5.6.16
      * Redis 3.0.5
    
    # Fixes:
    
      * Add /root/.skip_cleanup.cnf support
      * Add feature branch testing in HEAD
      * Avoid load spikes caused by long running tasks
      * Avoid race conditions on multi-line sed replacement -- fixes #806
      * Clean up any remaining procs zombies
      * Clean up postfix queue to get rid of bounced emails
      * Disable ioncube and opcache for HHVM
      * Disable Redis for Hostmaster in the backend
      * Do not allow to install non-standard OpenSSH on Ubuntu
      * Do not break /data/all/cpuinfo permissions on Octopus upgrade
      * Do not run 'apt-get autoremove' automatically
      * Do not use wrapper for dot-files cleanup
      * Document better BOA aggressive installation behavior -- fixes #811
      * Document boa in-octopus command -- fixes #817
      * Don't strip $args from $request_uri in redirects
      * Fix cron schedule for upgrades
      * Fix for broken Git on Ubuntu
      * Fix for not working PHP rebuild check
      * Fix for not working syncpass tool
      * Fix PHP deprecated warning in D8 -- fixes #804
      * Ignore 'env COLUMNS' sent by Drush remotely -- fixes #373
      * Ignore daily.sh in clear.sh
      * Improve _SQUEEZE_TO_WHEEZY procedure -- #627
      * Improve cron tasks schedule
      * Improve daily cleanup performance + support for /root/.giant_traffic.cnf
      * Improve devpts check -- fixes #788
      * Improve docs/MIGRATE.txt
      * Improve resolv.conf auto-recovery procedure
      * Improve system check -- fixes #811
      * Move Redis restart procedure to correct script
      * PHP: Add missing path to open_basedir for CLI
      * Remove debug code to not kill the initial install
      * Remove not working /etc/logrotate.d/lshell -- fixes #823
      * Update advagg auto configuration variables -- fixes #792
      * Update boa/lib/functions/helper.sh.inc with current OS -- fixes #787
      * Update FPM workers autoconf logic
      * Update the cache cleanup logic
      * Use better placeholder for solr_integration_module variable
      * Use correct DPkg::Options for dist-upgrade -- fixes #627
      * Use known MySQLTuner version -- fixes #827
      * Use LibYAML 0.1.6
      * Use opcache.restrict_api
      * Use sha256 for self-signed certs


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!