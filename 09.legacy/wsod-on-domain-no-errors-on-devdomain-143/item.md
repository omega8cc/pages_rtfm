---
title: WSOD on do.main &#8211; no errors on dev.do.main
slug: wsod-on-domain-no-errors-on-devdomain-143
menu: WSOD on do.main &#8211; no errors on dev.do.main
date: 31-01-2014
published: true
publish_date: 31-01-2014
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="debug-q"></a>

QI tried to debug WSOD issue by accessing my website with dev.do.main subdomain, but there are absolutely no PHP errors displayed and everything works, while without “dev” there is still WSOD!

<a name="debug-a"></a>

AThis problem can be typically solved by clearing all caches, either in the Aegir control panel, on the site’s performance admin page or via Drush with @drush cc all@ command. If the problem is permanent and clearing site’s caches or our automated Redis server daily restart didn’t help, its is recommended to switch to Redis modern mode with @redis_use_modern = TRUE@, @redis_flush_forced_mode = TRUE@ and @redis_lock_enable = TRUE@ in either “site or platform level INI file”:https://omega8.cc/how-to-control-boa-on-site-and-platform-level-293. It is also a good idea to review your contrib modules you have added or updated before the WSOD happened, to find which module could cause this issue.