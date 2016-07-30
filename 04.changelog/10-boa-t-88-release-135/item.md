---
# http://learn.getgrav.org/content/headers
title: 1.0-boa-T-8.8 release
slug: 10-boa-t-88-release-135
# menu: 1.0-boa-T-8.8 release
date: 15-07-2011
published: true
publish_date: 15-07-2011
# unpublish_date: 15-07-2011
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

The Omega8.cc team is happy to release Barracuda/Octopus Edition 1.0-boa-T-8.8. This Edition includes many new features, fixes and improvements introduced in the last six weeks since previous Edition.

### New Octopus platforms

 * Drupal 7.4
 * CiviCRM 3.4.4
 * CiviCRM 4.0.4
 * Videola 1.0-alpha1

### Updated Octopus platforms

 * OpenPublic 1.0-beta1 7.4
 * Drupal Commerce 1.0-beta4
 * Acquia Commons 1.7
 * Acquia 7.4.4
 * OpenScholar 2.0-beta11
 * Conference 1.0-beta1

### New features

 * Speed Booster can be disabled per site or per platform.
 * Redis/Memcached can be disabled per site or per platform.
 * Redis/Memcached chained cache enabled also for anonymous visitors.
 * Support for private\_upload module added.
 * Support for static sites/domain/files/robots.txt file per site #1173954.
 * New \_HTTP\_WILDCARD Barracuda option for Nginx configuration #1152316.
 * New \_XTRAS\_LIST Barracuda option to define extras to be used.
 * Scripts to add extra ftp or lshell standard or lshell master users.
 * New \_PLATFORMS\_LIST Octopus option to configure the list of platforms.
 * You can migrate sites between some install profiles by default:
 Drupal/Pressflow -> Acquia
 Acquia -> Drupal/Pressflow
 Acquia -> CiviCRM 3
 Cocomore/CDC/DrupalCenter -> Pressflow
 * New \_O\_CONTRIB\_UP Octopus option to upgrade last two contrib sets.

### Changes

 * Migration from commercedev to commerce\_kickstart profile.
 * More system info stored in BOA logs to help with debugging.
 * Nginx config – deny access to /hosting/c/server\_master.
 * Better how-to in the override.global.inc template.
 * Chive upgrade to 0.4.2.
 * Nginx upgrade to 1.0.4.

### Fixes

 * OpenPublic password policy issue fixed on site install.
 * OpenScholar missing libraries issue fixed.
 * Issue #1213094 – FServer platform missing module fixed.
 * Mollom problem when running via (SSL) proxy fixed.
 * Issue #1209150 – always use \_MY\_OWNIP when defined.
 * Issue #1208386 – fix for broken csf configuration template.
 * Boost cache write permissions after site migration fixed.
 * Nginx config – better support for CiviCRM.
 * Issue #1198572 – do not run SMTP check if \_SMTP\_RELAY\_HOST is set.
 * Forced PHP-FPM rebuild on MariaDB 5.2.7 upgrade.
 * Issue #1196006 – fixed Nginx X-Accel-Redirect support.
 * Security Issue #1197172 – bypass access restrictions to protected files fixed.
 * Issue #1182680 – fixed support for backup\_migrate module.
 * Issue #1182582 – fixed search paths for node.js, image.jpg etc.
 * Critical Issue #1183500 #1182660 – fall back to the wildcard * in Nginx.
 * Issue #962188 – Nginx version check in vhost.tpl.php now works.
 * Issue #1170498 – Extra config variable was missing in Nginx config templates.
 * Percona upgrade path fixed.
 * Broken dev version of the backup\_migrate module replaced with stable.
 * Use correct platforms versions numbers in the ftp symlinks.

You can read full changelog as always at: http://bit.ly/newboa

Enjoy!
