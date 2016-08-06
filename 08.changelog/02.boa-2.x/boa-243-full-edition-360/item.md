---
# http://learn.getgrav.org/content/headers
title: BOA-2.4.3 Full Edition
slug: boa-243-full-edition-360
menu: BOA-2.4.3 Full Edition
date: 19-05-2015
published: true
publish_date: 19-05-2015
# unpublish_date: 19-05-2015
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.4.3 Full Edition, focused on Aegir platforms update with latest Drupal core included. Enjoy!

 
    ### Stable BOA-2.4.3 Release - Full Edition
    ### Date: Tue May 19 13:40:40 PDT 2015
    ### Milestone URL: https://github.com/omega8cc/boa/milestones/2.4.3
    
      @=> Includes Aegir Hostmaster 2.x-head with improvements
      @=> Includes Aegir Provision 3.x-head with improvements
      @=> Includes Drush 7 customized for BOA
    
    # Release Notes:
    
      This BOA release is focused on Aegir platforms update with latest Drupal core
      included. There are also a few system updates and bug fixes, as listed below.
    
    # Changes:
    
      * Redis Integration Module: Update to version mod-08-05-2015
      * Use HTTPS intermediate mode to support legacy systems like XP/IE8 - see #718
    
    # System upgrades:
    
      * Drush mini-7-08-05-2015
      * MariaDB 10.0.19
      * MariaDB Galera Cluster 10.0.19
      * PHP 5.4.41
      * PHP 5.5.25
      * PHP 5.6.9
      * Redis 3.0.1
    
    # Fixes:
    
      * CiviCRM known bugs and regressions fixed
      * Improve drush aliases cleanup
      * Redis: sync net.core.somaxconn with tcp-backlog
      * sqlmagic: do not escape backslashes and EOL character - fixes #672


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!