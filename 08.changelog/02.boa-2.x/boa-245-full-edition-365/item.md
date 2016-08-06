---
title: BOA-2.4.5 Full Edition
slug: boa-245-full-edition-365
menu: BOA-2.4.5 Full Edition
date: 10-07-2015
published: true
publish_date: 10-07-2015
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.4.5 Full Edition, which includes PHP and Redis security upgrade plus four updated platforms. Enjoy!

 
    ### Stable BOA-2.4.5 Release - Full Edition
    ### Date: Fri Jul 10 11:25:43 PDT 2015
    ### Milestone URL: https://github.com/omega8cc/boa/milestones/2.4.5
    ### Latest hotfix added on: Fri Jul 10 14:49:11 PDT 2015
    
      @=> Includes Aegir Hostmaster 2.x-head with improvements
      @=> Includes Aegir Provision 3.x-head with improvements
      @=> Includes Drush 7 customized for BOA
    
    # Release Notes:
    
      This BOA release includes PHP security upgrade for versions 5.6, 5.5 and 5.4
      plus security upgrade for Redis server and four updated Octopus platforms.
    
      Support for Drupal 8 is temporarily removed, because now it would require
      an upgrade to Drush 8, which in turn completely removes support for PHP 5.3,
      while it's still more important to support legacy Pressflow 6 sites, if they
      are not ready to move beyond PHP 5.3 yet, than trying to support some
      (too fast) moving targets like Drupal 8 beta, and Drush 8 head.
    
    # Updated Octopus platforms:
    
      Commerce 2.26 ---------------- https://drupal.org/project/commerce_kickstart
      Commons 3.28 ----------------- https://drupal.org/project/commons
      OpenAtrium 2.43 -------------- https://drupal.org/project/openatrium
      Panopoly 1.25 ---------------- https://drupal.org/project/panopoly
    
    # Changes:
    
      * Drupal 8 is not supported until we can switch to Drush 8 and remove PHP 5.3
    
    # System upgrades:
    
      * Nginx 1.9.2
      * PHP 5.4.43
      * PHP 5.5.27
      * PHP 5.6.11
      * Redis 3.0.2


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!