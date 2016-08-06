---
# http://learn.getgrav.org/content/headers
title: BOA-2.0.1 Edition
slug: boa-201-edition-146
menu: BOA-2.0.1 Edition
date: 28-12-2011
published: true
publish_date: 28-12-2011
# unpublish_date: 28-12-2011
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

The Omega8.cc team is happy to release Barracuda/Octopus Edition BOA-2.0.1. This Edition includes a few important new features, three new platforms, twelve updated platforms and many fixes and improvements introduced in the last nine weeks since previous Edition.

### New Octopus platforms

 * ELMS 1.0-alpha5  
 * Open Deals 1.0-alpha4  
 * Open Outreach 1.0-beta6

### Updated Octopus platforms

 * Acquia 7.10.10  
 * Acquia Commons 2.3  
 * CiviCRM 3.4.8  
 * CiviCRM 4.0.8  
 * Commerce Kickstart 1.0-rc7  
 * Drupal 7.10  
 * Managing News 1.2.1  
 * NodeStream 1.1  
 * Open Atrium 1.1.1  
 * OpenChurch 1.22-a  
 * OpenScholar 2.0-beta13  
 * ProsePoint 0.41

### New features

 * Speed Booster Purge Server for all Drupal 6.x based platforms with automatically configured support for all devices caching.  
 * Enhanced Pressflow core for all bundled 6.22 based platforms, applied automatically also to already installed platforms: https://github.com/omega8cc/pressflow6  
 * Added access to the “clients” directory with shortcuts/symlinks to all hosted sites per Aegir “client”.

### New o\_contrib modules

 * ESI for Nginx SSI – http://drupal.org/sandbox/mikeytown2/1328648  
 * Purge for Speed Booster – http://drupal.org/project/purge  
 * Expire for Speed Booster – http://drupal.org/project/expire

### Changes

 * Nginx upgrade to 1.0.11  
 * MariaDB upgrade to 5.2.10  
 * Percona upgrade to 5.5.18  
 * Chive upgrade to 1.0.1  
 * Pure-FTPd upgrade to 1.0.35  
 * The syslog module is no longer enabled by default and added to the list of automatically disabled modules.

### Fixes

 * Mobile devices detection and caching improved.  
 * Many fixes and enhancements for Speed Booster caching logic.  
 * Many fixes and enhancements for Boost caching logic.  
 * More reliable Nginx auto-healing.  
 * Broken symlinks in the “clients” directory are now purged daily.  
 * The preg\_match for dev should check for dev. and devel. only.  
 * Issue #1366564 – Use instance specific .octopus.cnf files.  
 * Issue #1262988 – Use reliable test for upload progress availability.  
 * Issue #1350028 – Make sure that all BOA pid files are removed on reboot.  
 * Issue #1348906 – BOND script outdated \_INSTALLER\_VERSION variable fixed.  
 * Issue #1321428 – Make sure that \_SSH\_PORT is written in /etc/ssh/sshd\_config.

You can read full changelog as always at: http://bit.ly/newboa

Enjoy!