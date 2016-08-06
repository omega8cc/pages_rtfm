---
title: BOA-2.4.9 Full Edition
slug: boa-249-full-edition-374
menu: BOA-2.4.9 Full Edition
date: 27-02-2016
published: true
publish_date: 27-02-2016
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.4.9 Full Edition, which includes latest Drupal 7 and Pressflow 6 security updates, along with bug fixes and other system software updates. Enjoy!

 
    ### Stable BOA-2.4.9 Release - Full Edition
    ### Date: Sat Feb 27 15:22:11 GMT 2016
    ### Milestone URL: https://github.com/omega8cc/boa/milestones/2.4.9
    
      @=> Includes Aegir Hostmaster 2.x-head with improvements
      @=> Includes Aegir Provision 3.x-head with improvements
      @=> Includes Drush 7 customized for BOA
    
    # Release Notes:
    
      This BOA release includes latest Drupal 7 and Pressflow 6 security updates,
      along with bug fixes and other system software updates.
    
      @=> All supported Aegir platforms have been updated to their latest releases
    
      @=> What are BOA plans for Drupal 6 support after February 24th, 2016?
    
          We will support Drupal/Pressflow 6 in all new releases, as long as
          available PHP versions will allow to use it (we run our own Pressflow 6
          based site on PHP 5.6 for many months with zero issues). For more details
          please check: https://github.com/omega8cc/boa/issues/824
    
      @=> Even if deprecated PHP versions are still included in this release,
          any Octopus instance running PHP older than 5.5 will not be able to
          receive upgrade to BOA-2.4.9, as announced before -- Please switch your
          Octopus to PHP 5.6 or at least 5.5 to be able to upgrade not only
          the Barracuda system part of BOA, but also Octopus Satellite --
          The how-to can be found at: https://omega8.cc/node/330
    
      @=> Drupal 8 support for custom platforms in the ~/static directory tree
          will be included, along with Drush 8 and Hostmaster 3.x in the upcoming
          BOA-3.0.0 release: https://github.com/omega8cc/boa/milestones/3.0.0
          Note: BOA will not include built-in Drupal 8 platforms until Drupal 8
          will support symlinks in the codebase, like all previous core versions
    
    # System upgrades:
    
      * MariaDB Galera Cluster 10.0.24
      * Nginx 1.9.12
    
    # Fixes:
    
      * Do not force Ruby with RVM for root on every upgrade
      * SQL max_user_connections autoconf value can be too low -- fixes #873


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!