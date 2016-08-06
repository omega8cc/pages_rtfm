---
title: How to use robots.txt properly?
slug: how-to-use-robotstxt-properly-243
menu: How to use robots.txt properly?
date: 12-05-2015
published: true
publish_date: 12-05-2015
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="robots-q"></a>

QThere is no access to the platform root directory in all built-in platforms, so how can I manage robots.txt per site in the multisite setup used in Aegir?

<a name="robots-a"></a>

AThe standard robots.txt file can’t be used effectively in the multisite environment, because it would be shared between all sites on the same platform. BOA system will delete this file if it exists and enable the built-in “RobotsTxt module”:http://drupal.org/project/robotstxt instead.

<a name="robots-b"></a>

!Note that BOA system not only enables the RobotsTxt module automatically every morning (server time zone). It also creates the static file `/sites /foo.com /files /robots.txt` for every site hosted, and since any further modifications in the module configuration will not update the static file directly, you should delete it to make the new settings active, and BOA system will then create it again, next morning, using updated module configuration. Furthermore, BOA will delete this file and re-create if it’s older than 7 days, so you always need to update it via module and never directly, or your changes will be overwritten when the file is regenerated via module.

<a name="robots-c"></a>

»You can even use separate, extra (never maintained via RobotsTxt and never deleted nor regenerated, though) robots.txt files per every site alias, which may be useful for sites using Domain Access to manage virtual sub-sites. BOA system will automatically map `/robots.txt` requests to `/sites /foo.com /files /foo.com.robots.txt` if exists, and fallback to default file it generates for you in `/sites /foo.com /files /robots.txt` otherwise.