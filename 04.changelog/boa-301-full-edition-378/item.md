---
# http://learn.getgrav.org/content/headers
title: BOA-3.0.1 Full Edition
slug: boa-301-full-edition-378
# menu: BOA-3.0.1 Full Edition
date: 11-04-2016
published: true
publish_date: 11-04-2016
# unpublish_date: 11-04-2016
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

We are happy to release BOA-3.0.1 Full Edition, which includes complete Aegir 3 with Drush 8, and supports latest Drupal 8, along with many important fixes and improvements. Enjoy!

 
    ### Stable BOA-3.0.1 Release - Full Edition
    ### Date: Mon Apr 11 18:49:43 PDT 2016
    ### Milestone URL: https://github.com/omega8cc/boa/milestones/3.0.1
    
      @=> Includes Aegir Hostmaster 3.x-head with improvements
      @=> Includes Aegir Provision 3.x-head with improvements
      @=> Includes Drush 8 customized for BOA
    
    # Release Notes:
    
      This BOA release includes important fixes and improvements in the upgrade
      procedure from BOA-2.4.9 and in the initial install procedures, along with
      support for latest Drupal 8.0.x and 8.1.x as custom platforms you can create
      in the ~/static directory tree. We list here also all hot-fixes applied
      after initial BOA-3.0.0 release.
    
      @=> BOA will not include built-in Drupal 8 platforms until Drupal 8 will
          support symlinks in the codebase, like all previous core versions.
    
      @=> Octopus Aegir instances hosted on Power Engine option will *not* receive
          upgrade to BOA-3.x unless requested via https://omega8.cc/support
          to prevent issues with (often) customized Hostmaster modules not ready
          for Drupal 7 based Aegir control panel. All hosted BOA systems will still
          continue to receive the Barracuda system upgrades.
    
      @=> It is possible to host previous stable BOA-2.4.9 Octopus instances
          on systems with Barracuda upgraded to BOA-3.0.1
    
    # Known problems:
    
      https://github.com/omega8cc/boa/milestones/3.0.2
    
    # New features and enhancements:
    
      * Allow boa in-octopus to specify version {stable|head|2.4}
    
    # Changes:
    
      * Allow to execute compass over SSH
      * Allow to upload dot-files via SFTP
      * Remove/don't install not used blocks in Hostmaster
    
    # System upgrades:
    
      * Add mydropwizard-6.x-1.4 to all existing D6 platforms
      * Drush micro-8-08-04-2016
      * Lshell 0.9.18.3 -- #895
      * Nginx 1.9.14
      * PHP 5.5.34
      * PHP 5.6.20
      * PHP 7.0.5 (for testing only)
      * Redis module 7.x-3.12
    
    # Fixes:
    
      * 3.0.0 clean install is broken -- #899
      * boa in-2.4 fails to install on Debian Jessie -- #898
      * Can't git pull -- #890
      * CiviCRM error on verification D6 site -- #897
      * D7 API compatibility fix for node_save() in Hostmaster
      * Do not switch default PHP to 7.0 if installed
      * Drush issues: no aliases available -- #887
      * Fix for 3.x to 3.x upgrades
      * Fix for FPM master proc monitor
      * Fix for input filters upgrade path
      * Fix for series test to avoid downgrade attempts
      * Fix the legacy install mode -- #898
      * Less and more no longer allowed -- #896
      * Limit the list of allowed_shell_escape commands
      * Missing VBO options -- #892
      * Overlay header title not showing -- #889
      * Problems installing rvm / compass -- #895
      * Remove deprecated sftp restriction
      * Require BOA-2.4.9 before upgrade to BOA-3.x also in barracuda -- #886
      * Switch octopus upgrade mode automatically to legacy if needed
      * tar and gunzip fails because of permission denied -- #894
      * Use Drush 8 on command line -- #887
      * vi and vim both open nano instead of vim -- #893


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!