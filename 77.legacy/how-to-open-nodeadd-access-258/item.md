---
# http://learn.getgrav.org/content/headers
title: How to open node/add access?
slug: how-to-open-nodeadd-access-258
# menu: How to open node/add access?
date: 11-05-2013
published: true
publish_date: 11-05-2013
# unpublish_date: 11-05-2013
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="node-q"></a>

QHow to open access to node/add for not logged in visitors if our workflow requires this, while now they are simply redirected to the homepage?

<a name="node-a"></a>

AThis has been restricted by design to protect your sites from brute-force DoS attempts, because this URL is never cached and always hits Drupal directly. There is an easy to use switch to disable it per site or per platform, so anonymous visitors will be able to create nodes again – just set ` allow_anon_node_add = TRUE` in the site or platform level “INI file”:https://omega8.cc/how-to-control-boa-on-site-and-platform-level-293

<a name="node-b"></a>

!Please understand that by removing this default protection, you are making all sites hosted on your instance vulnerable to potential DoS attacks, which are very common these days, with networks of spambots targeting Drupal sites with attempts to add spam as nodes, comments and registering new accounts. We reserve the right to restore default protection if our monitoring will detect that removed restrictions allowed to successfully attack your site and cause system instability.