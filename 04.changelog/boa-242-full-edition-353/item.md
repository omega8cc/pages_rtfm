---
# http://learn.getgrav.org/content/headers
title: BOA-2.4.2 Full Edition
slug: boa-242-full-edition-353
# menu: BOA-2.4.2 Full Edition
date: 27-04-2015
published: true
publish_date: 27-04-2015
# unpublish_date: 27-04-2015
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

 We are happy to release BOA-2.4.2 Full Edition, with 15 updated Aegir platforms, 13 new software versions, plus over 23 bug fixes and improvements. Enjoy!

 
    ### Stable BOA-2.4.2 Release - Full Edition
    ### Date: Mon Apr 27 11:12:09 PDT 2015
    ### Milestone URL: https://github.com/omega8cc/boa/milestones/2.4.2
    ### Latest hotfix added on: Fri May  1 02:07:54 PDT 2015
    
      @=> Includes Aegir Hostmaster 2.x-head with improvements
      @=> Includes Aegir Provision 3.x-head with improvements
      @=> Includes Drush 7 customized for BOA
    
    # Release Notes:
    
      This BOA release includes 15 updated Aegir platforms with latest Drupal core,
      2 new features and enhancements, 13 new software versions, 3 other changes,
      plus over 20 bug fixes.
    
    # Updated Octopus platforms:
    
      aGov 1.7 --------------------- https://drupal.org/project/agov
      Commerce 1.36 ---------------- https://drupal.org/project/commerce_kickstart
      Commerce 2.23 ---------------- https://drupal.org/project/commerce_kickstart
      Commons 2.24 ----------------- https://drupal.org/project/commons
      Commons 3.25 ----------------- https://drupal.org/project/commons
      Guardr 2.11 ------------------ https://drupal.org/project/guardr
      OpenAid 2.1 ------------------ https://drupal.org/project/openaid
      OpenAtrium 2.33 -------------- https://drupal.org/project/openatrium
      OpenChurch 1.17-b2 ----------- https://drupal.org/project/openchurch
      OpenChurch 2.1-b7 ------------ https://drupal.org/project/openchurch
      OpenOutreach 1.19 ------------ https://drupal.org/project/openoutreach
      OpenPublic 1.5 --------------- https://drupal.org/project/openpublic
      Panopoly 1.21 ---------------- https://drupal.org/project/panopoly
      Recruiter 1.6 ---------------- https://drupal.org/project/recruiter
      Restaurant 1.0-b12 ----------- https://drupal.org/project/restaurant
    
      @=> NOTE: Drupal 8 support is broken in this release, because latest Drush
          doesn't support older Drupal 8 beta versions, while new D8 beta is not
          released and tested yet, and we really need latest Drush to fix broken
          D6->D7 upgrade path, so we could prepare for full Aegir 3, which comes
          with D7 in the frontend.
    
    # New features and enhancements:
    
      * Re-create files/robots.txt if older than 7 days
      * Restore default DNS when /root/.use.default.nameservers.cnf exists
    
    # Changes:
    
      * Enable SPDY and PFS by default - fixes #545
      * Use GitLab as a secondary mirror
      * Whitelist drush pm-updatestatus
    
    # System upgrades:
    
      * cURL 7.42.1 (if installed from sources)
      * Drush mini-7-25-04-2015
      * Duplicity 0.7.02 (please run 'backboa install' to upgrade)
      * MariaDB 5.5.43
      * MariaDB Galera Cluster 10.0.17
      * MySecureShell master-20-03-2015
      * Nginx 1.8.0
      * OpenSSH 6.8p1 (if installed from sources)
      * OpenSSL 1.0.2a (if installed from sources)
      * PHP 5.6.8, 5.5.24, 5.4.40
      * PHPRedis master-18-03-2015
      * Redis 3.0.0
      * Ruby 2.2.2
    
    # Fixes:
    
      * Add service cron start to migrate docs - fixes #654
      * BOA.sh.txt should update installers when invoked interactively - fixes #644
      * Do not add Google DNS when custom DNS is expected
      * Do not count requests for images derivatives if private files mode is used
      * Do not create conflicting plain HTTP proxy for single IP mode - fixes #465
      * Force csf/lfd update before and after running barracuda upgrade - fixes #685
      * How to enable permanent redirect to HTTPS with single IP - #465
      * Improve DNS self-healing magic - see #674
      * Improve FPM auto-healing to properly detect conflicting instances
      * Make sure that dl mirrors never get blocked
      * Nginx: Stop the POST flood to /autodiscover/autodiscover.xml
      * Nginx: Use dummy db fastcgi_param placeholders if any of them is empty
      * Remove aggresive firewall cleanup - fixes #688
      * Remove onetime fix intended to sync new defaults - fixes #678
      * Update absolute URLs to files for sites cloned/migrated/renamed
      * Update composer on barracuda upgrade
      * Use _TOMCAT_TO_JETTY=NO in cnf template to avoid confusion - see #676
      * Use correct placeholder in the xboa proxy - fixes #655
      * Use MAIN_SITE_NAME instead of possibly fake SERVER_NAME - see #385
      * Where to add the SSL redirect configuration snippet - fixes #681


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!