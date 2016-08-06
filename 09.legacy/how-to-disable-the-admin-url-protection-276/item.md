---
title: How to disable the /admin* URL protection?
slug: how-to-disable-the-admin-url-protection-276
menu: How to disable the /admin* URL protection?
date: 16-07-2013
published: true
publish_date: 16-07-2013
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="admin-q"></a>

QHow to disable the /admin * URL protection, if it keeps redirecting me to the site homepage even if I’m logged in, probably because of some module which affects cookies handling?

<a name="admin-a"></a>

AThis has been restricted by design to protect your sites from brute-force DoS attempts, because these URLs are never cached and always hit Drupal directly. There is an easy to use switch to disable this protection per site, so if you experience problems with redirects to the homepage when accessing /admin * URLs, just set `disable_admin_dos_protection = TRUE` in the site or platform level “INI file”:https://omega8.cc/how-to-control-boa-on-site-and-platform-level-293 — note however that we recommend to debug this and determine the module affecting Drupal standard cookies naming and behaviour, so you could keep your site safe from DoS attempts.

<a name="admin-b"></a>

!Please understand that by removing this default protection, you are making all sites hosted on your instance vulnerable to potential DoS attacks, which are very common these days, with networks of spambots targeting Drupal sites with attempts to add spam as nodes, comments and registering new accounts. We reserve the right to restore default protection if our monitoring will detect that removed restrictions allowed to successfully attack your site and cause system instability.