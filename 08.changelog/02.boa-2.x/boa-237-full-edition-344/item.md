---
title: BOA-2.3.7 Full Edition
slug: boa-237-full-edition-344
menu: BOA-2.3.7 Full Edition
date: 25-11-2014
published: true
publish_date: 25-11-2014
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.3.7 Full Edition, with includes updated versions of all supported Drupal  
 platforms to provide latest Drupal 7.34 and Pressflow 6.34 cores and many fixes and improvements.

 
    ### Stable BOA-2.3.7 Release - Full Edition
    ### Date: Tue Nov 25 15:44:48 PST 2014
    ### Includes Aegir 2.x-head with improvements
    
    # Release Notes:
    
      This new BOA release includes updated versions of all supported Drupal
      platforms to provide latest Drupal 7.34 and Pressflow 6.34 cores, plus
      new features, improvements and bug fixes.
    
      We recommend that you upgrade your D7 sites using this safe workflow:
    
        https://omega8.cc/your-drupal-site-upgrade-safe-workflow-298
    
      For up-to-date information on #Drupageddon please check:
    
        https://omega8.cc/drupageddon-psa-2014-003-342
    
    # Updated Octopus platforms:
    
      Commerce 1.32 ---------------- https://drupal.org/project/commerce_kickstart
      Commerce 2.20 ---------------- https://drupal.org/project/commerce_kickstart
      Commons 2.21 ----------------- https://drupal.org/project/commons
      Commons 3.20 ----------------- https://drupal.org/project/commons
      Guardr 2.5 ------------------- https://drupal.org/project/guardr
      Open Atrium 2.25 ------------- https://drupal.org/project/openatrium
      Open Outreach 1.13 ----------- https://drupal.org/project/openoutreach
      Panopoly 1.14 ---------------- https://drupal.org/project/panopoly
    
    # New features and enhancements in this release:
    
      * Support for locking/unlocking web server write access in all codebases.
    
    # System upgrades in this release:
    
      * MariaDB 10.0.15
    
    # Fixes in this release:
    
      * Allow any single site to use 1/2 of available SQL connections max.
      * Clean up dot files after installing or updating RVM.
      * Do not run extra updates on systems running latest head version.
      * Improve ghost sites cleanup.
      * Issue #467 - Centralize control files outside of codebases tree.
      * Issue #498 - ERPAL: Fatal error: Unsupported operand types.
      * Issue #499 - RVM: Add oily_png gem version 1.1.1
      * Issue #504 - Add docs/RVM.txt
      * Issue #504 - Remove ~/.rvm/scripts/notes script breaking lshell.
      * Issue #509 - Do not delete anything from hostmaster site level modules.
      * It is safe to run manage_ltd_users every minute.
      * Never touch hostmaster aliases and vhosts even they appear broken.
      * Use gnupg2 by default.
      * Use latest Ruby 2.1.x or 2.0.x available.
      * Use verbose RVM install mode to improve debugging.


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!