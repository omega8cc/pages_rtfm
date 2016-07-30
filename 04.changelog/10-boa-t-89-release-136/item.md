---
# http://learn.getgrav.org/content/headers
title: 1.0-boa-T-8.9 release
slug: 10-boa-t-89-release-136
# menu: 1.0-boa-T-8.9 release
date: 30-07-2011
published: true
publish_date: 30-07-2011
# unpublish_date: 30-07-2011
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

The Omega8.cc team is happy to release Barracuda/Octopus Edition 1.0-boa-T-8.9. This Edition includes a few critical fixes and improvements introduced in the last two weeks since previous Edition.

### Updated Octopus platforms

 * Drupal 7.7
 * Open Atrium 1.0
 * OpenPublic 1.0-beta1 7.7
 * Drupal Commerce 1.0-rc1
 * Acquia 7.7.5
 * ProsePoint 0.40

### Fixes

 * Two critical cache related bugs fixed in Nginx 1.0.5.
 * Critical Issue #1222208 – broken web-based cron for sites.
 * Issue #1223506 – cloning a site looses client site ownership.
 * Missing jquery.ui symlink in Conference COD breaks install.
 * Issue #1230420 – do not purge /tmp too aggressively.
 * Issue #1234470 – SSL proxy didn’t respect HTTP wildcard.
 * Boost’s false alarm about permissions silenced.
 * Permissions for sites/domain/private/ * also fixed daily.

### Changes

 * Nginx upgrade to 1.0.5.
 * Chive upgrade to 0.5.1.
 * Web-based method set by default for sites cron in Aegir.

You can read full changelog as always at: http://bit.ly/newboa

Enjoy!
