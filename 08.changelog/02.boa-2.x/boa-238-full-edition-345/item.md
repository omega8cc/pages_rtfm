---
title: BOA-2.3.8 Full Edition
slug: boa-238-full-edition-345
menu: BOA-2.3.8 Full Edition
date: 28-11-2014
published: true
publish_date: 28-11-2014
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.3.8 Full Edition, with includes updated versions of all supported Drupal  
 platforms to provide latest Drupal 7.34 and Pressflow 6.34 cores, new features and fixes.

 
    ### Stable BOA-2.3.8 Release - Full Edition
    ### Date: Sat Nov 29 09:58:45 SGT 2014
    ### Includes Aegir 2.x-head with improvements
    
    # Release Notes:
    
      This new BOA release includes new features, improvements and bug fixes.
    
    #-### Support for optional Drupalgeddon daily checks on all hosted D7 sites
    
      ~/static/control/drupalgeddon.info
    
      Previously enabled by default, now requires this control file to still
      run daily, because it may generate some false positives not always possible
      to avoid or silence, so it no longer makes sense to run this check daily,
      especially after BOA has run it automatically for a month and finally even
      disabled automatically all clearly compromised sites.
    
      Note that your system administrator may still enable this with root level
      control file /root/.force.drupalgeddon.cnf, so it will still run, even
      if you will not create the Octopus instance level empty control file:
      ~/static/control/drupalgeddon.info
    
      Please note that current version of Drupalgeddon Drush extension needs
      the 'update' module to be enabled to avoid even more false positives,
      so BOA will enable the 'update' module temporarily while running this
      check, which in turn will result with even more e-mails notices sent
      to the site admin e-mail, if these notices are enabled.
    
    #-### Support for automated BOA upgrades: weekly and one-time
    
      You can configure BOA to run automated upgrades to latest stable version
      for both Barracuda and all Octopus instances with three variables, empty
      by default. All three variables must be defined to enable auto-upgrade.
      You can set _AUTO_UP_MONTH and _AUTO_UP_DAY to any date in the past
      if you wish to enable only weekly system upgrades.
    
      Remember that one-time upgrades will include complete upgrade to latest BOA
      stable for Barracuda and all Octopus instances, while weekly upgrade is
      designed to run only 'barracuda up-stable system' upgrade.
    
      _AUTO_UP_WEEKLY= #------ Day of week (1-7) for weekly system upgrades
      _AUTO_UP_MONTH= #------- Month (1-12) to define date of one-time upgrade
      _AUTO_UP_DAY= #--------- Day (1-31) to define date of one-time upgrade
    
      All three variables should be added in your /root/.barracuda.cnf file.
    
    # Updated Octopus platforms:
    
      ERPAL 2.2 -------------------- https://drupal.org/project/erpal
    
    # New features and enhancements in this release:
    
      * Support for automated BOA upgrades: weekly and one-time.
    
    # Changes in this release:
    
      * Drupalgeddon daily checks on all hosted D7 sites are now optional.
    
    # Fixes in this release:
    
      * Issue #508 - The _EASY_HOSTNAME is not required in local install mode.
      * Issue #516 - Do not break binaries detection with 'which'.


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!