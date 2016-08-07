---
title: TITLE
slug: URI
menu: MENU
date: 08-08-2016
published: true
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /URI
---

How to Allow "node/add" Anonymous Access

By default, anonymous visitors cannot access any @node/add@ path on a
site managed with a version of Aegir which comes with "BOA":boa.

h2. Task: Allow Anonymous "node/add" Access

However, you can enable anonymous access by
 *creating an empty control file* in the site-specific directory.
If your domain is @foo.com@, the file would be:

@sites/foo.com/modules/allow_anon_node_add.info@

This feature helps if the site's workflow involves the creation of new nodes
by visitors who aren't logged in. (This is typical for e-commerce
and community news sites.)

h2. More Information

h3. Why Is Anonymous "node/add" Access Blocked?

A page with a @node/add@ path is never cached, so Drupal has to
rebuild the page on-the-fly on every request. Any page that Drupal builds
like that is a risk for a brute-force Denial of Service attack. An attacker
could bring your site down by accessing these pages with hundreds or
thousands of hits in a very short time.

Thus, the default "BOA":boa protection is to restrict @node/add@ access to
logged-in users. Most workflows require that a user log in before
adding a node, so this system usually works fine.

[boa]
