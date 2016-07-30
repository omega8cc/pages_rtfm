---
# http://learn.getgrav.org/content/headers
title: BOA-3.0.0 Full Edition
slug: boa-300-full-edition-377
# menu: BOA-3.0.0 Full Edition
date: 30-03-2016
published: true
publish_date: 30-03-2016
# unpublish_date: 30-03-2016
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

 We are happy to release BOA-3.0.0 Full Edition, which includes complete Aegir 3 with Drush 8, and introduces full support for latest Drupal 8, along with many system software updates. Enjoy!

 
    ### Stable BOA-3.0.0 Release - Full Edition
    ### Date: Wed Mar 30 10:48:54 PDT 2016
    ### Milestone URL: https://github.com/omega8cc/boa/milestones/3.0.0
    ### Latest hotfix added on: Wed Apr  6 17:40:12 PDT 2016
    
      @=> Includes Aegir Hostmaster 3.x-head with improvements
      @=> Includes Aegir Provision 3.x-head with improvements
      @=> Includes Drush 8 customized for BOA
    
    # Release Notes:
    
      This BOA release includes complete Aegir 3 with Drush 8, and introduces
      full support for latest Drupal 8.0.5 and Drupal 8.1.0-beta2 as custom
      platforms you can create in the ~/static directory tree.
    
      @=> BOA will not include built-in Drupal 8 platforms until Drupal 8 will
          support symlinks in the codebase, like all previous core versions.
    
      @=> All supported Aegir platforms have been updated to their latest releases
    
      @=> Octopus Aegir instances hosted on Power Engine option will *not* receive
          upgrade to BOA-3.x unless requested via https://omega8.cc/support
          to prevent issues with (often) customized Hostmaster modules not ready
          for Drupal 7 based Aegir control panel. All hosted BOA systems will still
          continue to receive the Barracuda system upgrades.
    
      @=> It is possible to host previous stable BOA-2.4.9 Octopus instances
          on systems with Barracuda upgraded to BOA-3.0.0
    
    # Known problems:
    
      https://github.com/omega8cc/boa/milestones/3.0.1
    
      While clean 3.0.0 install worked in our tests before the release, it doesn't
      work for others. Until this problem is fixed properly without regressions,
      we are switching boa installer back to 2.4.9, which makes getting 3.0.0
      on initial installation a two step operation: first 'boa in-stable' install
      to get 2.4.9, and then 'barracuda up-stable' plus 'octopus up-stable' upgrade
      to get 3.0.0, because upgrades for barracuda and octopus from 2.4.9 to 3.0.0
      work fine.
    
      This also means that 'boa in-octopus' will still install the legacy 2.4.9
      octopus extra instances, and you can upgrade them to 3.0.0 with standard
      'octopus up-stable' mode.
    
      It is still possible to test/debug boa 3.0.0 clean installs -- just create
      an empty /root/.debug-boa-installer.cnf file before running the installer.
    
    # New features and enhancements:
    
      * Add Hosting Git optional feature -- fixes #753
      * Add mydropwizard module to D6 o_contrib by default
      * Add support for ap-northeast-2 Asia Pacific (Seoul) S3
      * Add support for PHP 7.0 -- experimental ! -- fixes #716
      * Add support for VServer kernel 4.1.19-vs2.3.8.4-beng
      * BOA with Aegir Hostmaster 3.x -- fixes #715
      * Switch to Drush 8 for Drupal 8 -- fixes #729
      * Allow to randomize duplicity full backup schedule
      * Monitor and block SSH connections flood
      * Run registry-rebuild in drush_provision_drupal_post_provision_deploy()
    
    # Changes:
    
      * Add linkchecker module to Contrib [F]orce[D]isabled
      * Deny sudo/su switch if used for root access - fixes #879
      * Do not install / remove auditd on VServer systems
      * Do not install / remove udev on VServer systems
      * Merge hosting_advanced_cron into Aegir core cron
      * Use Redis 7.x-3.x integration module
    
    # System upgrades:
    
      * Boto 2.39.0-fix-python-2.7.9 (please run 'backboa install' to upgrade)
      * CSF 8.16
      * Drush mini-8-08-03-2016
      * Duplicity 0.7.06 (please run 'backboa install' to upgrade)
      * Lshell 0.9.18.3
      * MongoDB database driver 1.6.13 for all PHP versions 
    <p>
    You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt</p>
    <p>Enjoy!</p>