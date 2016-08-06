---
title: BOA-2.4.6 Full Edition
slug: boa-246-full-edition-366
menu: BOA-2.4.6 Full Edition
date: 19-09-2015
published: true
publish_date: 19-09-2015
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.4.6 Full Edition, which includes several important system upgrades and  
 bug fixes, plus platforms with latest Drupal cores. Enjoy!

 
    ### Stable BOA-2.4.6 Release - Full Edition
    ### Date: Sat Sep 19 11:09:09 PDT 2015
    ### Milestone URL: https://github.com/omega8cc/boa/milestones/2.4.6
    
      @=> Includes Aegir Hostmaster 2.x-head with improvements
      @=> Includes Aegir Provision 3.x-head with improvements
      @=> Includes Drush 7 customized for BOA
    
    # Release Notes:
    
      This BOA release includes several important system upgrades and bug fixes.
      All supported Aegir platforms have been updated with latest Drupal cores.
    
      @=> Latest Drupal 8.0.0-beta15 works great, but currently only when installed
          as a custom platform in the ~/static directory tree, because it is not
          really symlinks-friendly. We will re-introduce built-in Drupal 8 platforms
          once this situation is improved.
    
    # Changes:
    
      * Add Twig C extension to PHP - v.1.22.1
      * Allow to customize auto-upgrades mode
      * Disable support for broken OpenScholar and Recruiter
      * Open default Postgres port for outgoing connections
      * Remove support for deprecated Feature Server distro
      * Remove support for deprecated OpenAcademy distro
      * Remove support for deprecated OpenBlog distro
      * Remove support for deprecated OpenChurch v.1 distro
      * Remove support for deprecated OpenDeals distro
      * Use distro specific Drupal core for problematic distros
    
    # System upgrades:
    
      * cURL 7.44.0 (if installed from sources)
      * Duplicity 0.7.05 (please run 'backboa install' to upgrade)
      * Jetty 7.6.17.v20150415
      * Jetty 8.1.17.v20150415
      * MariaDB 10.0.21
      * MariaDB 5.5.45
      * MariaDB Galera Cluster 10.0.21
      * Nginx 1.9.4
      * OpenSSH 7.1p1 (if installed from sources)
      * PHP 5.6.13, 5.5.29, 5.4.45
      * PHP: ionCube loader 5.0.18
      * Pure-FTPd 1.0.42
      * Redis 3.0.4
      * Ruby 2.2.3, 2.0.0-p647
      * Use pecl-jsmin-1.1.0
    
    # Fixes:
    
      * Allow to re-install deleted D7/D6 platforms when dev doesn't exist
      * Do not install phpunit -- it adds many PHP tools we don't need
      * Fix apache cleanup
      * Fix invalid regex in the INI docs
      * Improve auto-healing for SSHd
      * Improve Nginx DoS an DDoS protection
      * Improve pdnsd auto-healing
      * Improve SSL Docs to add more detail about multidomain certificates #757
      * Issue #766 - Fix for broken boa in-octopus procedure
      * Nginx: Fix support for s3/files/styles (s3fs)
      * Sync .htaccess with D7 core
      * Sync keywords for exceptions in daily.sh with global.inc
      * Use short sleep on firewall temp blocks cleanup


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!