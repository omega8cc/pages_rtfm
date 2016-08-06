---
title: How to debug failed Migrate task?
slug: how-to-debug-failed-migrate-task-328
menu: How to debug failed Migrate task?
date: 14-08-2014
published: true
publish_date: 14-08-2014
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="debug-q"></a>

QWhy Migrate task failed for a site I have tried to upgrade to new codebase with contrib modules moved to a different directory tree, for example from platform sites/all to installation profile?

<a name="debug-a"></a>

AIf you re-use the same name for newly created site or you are migrating a site to a new platform with modules moved to different subdirectories, for example from @sites/all/modules@ to @profiles/myprofile/modules@ and some of them use PHP includes, so their paths are registered also in Redis cache, it may cause fatal errors until you will temporarily disable Redis in the affected site “active INI file”:https://omega8.cc/how-to-control-boa-on-site-and-platform-level-293. How is this possible and how to avoid this? The explanation and a fix is very simple. Redis uses a site (domain) name as a cache key, and unlike it is with mysql based cache tables, which simply get away when the database is renamed or re-created, the Redis cache entries may stay in memory a bit longer, even until the system will restart Redis server, if the site didn’t clear them completely before it got renamed or deleted and then re-created with its name re-used. When you re-use the same name for a site, or when you are migrating a site to a new codebase with contrib modules moved around, the site will happily re-use cache leftovers still existing in Redis memory, which may cause serious problems and break the task in Aegir, because paths to PHP includes change on the fly as a result. “Disable Redis temporarily”:https://omega8.cc/how-to-disable-all-caching-and-aggregation-115#debug-c in the affected site and try to run the task again.

<a name="debug-b"></a>

»To avoid this problem we usually recommend to use unique, but different domain names for your sites (live and clones) and then add live domains only as aliases, because this way the keys in the cache (and vhosts) will always stay with the local (and unique) site name, and moving the alias between sites will not cause problems with cache leftovers or confusing paths in vhosts. For example: _sept-24.other-domain.com_, _sept-25.other-domain.com_ +alias: _live-domain.com_, etc.