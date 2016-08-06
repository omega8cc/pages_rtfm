---
title: 1.0-boa-T-8.10 release
slug: 10-boa-t-810-release-141
menu: 1.0-boa-T-8.10 release
date: 05-09-2011
published: true
publish_date: 05-09-2011
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

The Omega8.cc team is happy to release Barracuda/Octopus Edition 1.0-boa-T-8.10. This Edition includes one new platform, a few updated platforms and some fixes and improvements introduced in the last five weeks since previous Edition.

### New Octopus platform

 * OpenChurch 1.21

### Updated Octopus platforms

 * Acquia 7.7.6  
 * Acquia Commons 2.0  
 * CiviCRM 3.4.5  
 * CiviCRM 4.0.5  
 * Conference 1.0-beta2  
 * Drupal 7.8  
 * Drupal Commerce 1.0  
 * OpenPublic 1.0-beta2 7.8  
 * Ubercart 2.6 6.22

### Changes

 * Drush Make upgrade to 2.3  
 * Drush upgrade to 4.5  
 * Nginx upgrade to 1.0.6  
 * MariaDB upgrade to 5.2.8  
 * Higher limit\_conn for AdvAgg to support high async connections rate.

### Fixes

 * Tomcat runs as a separate ‘tomcat’ user instead of root.  
 * Issue #1250448 – Textile 7 requires Vars module.  
 * Issue #1248432 – support for CNAME records in the DNS check.

### New features

 * HTTP/HTTPS redirects example in the override.global.inc file.  
 * Enabled by default HTTPS and HTTP sessions/cookies for D7.  
 * Issue #1243068 – Allow to override $cache\_module\_path.

You can read full changelog as always at: http://bit.ly/newboa

Enjoy!