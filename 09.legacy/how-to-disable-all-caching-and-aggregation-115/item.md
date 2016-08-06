---
title: How to disable all caching and aggregation?
slug: how-to-disable-all-caching-and-aggregation-115
menu: How to disable all caching and aggregation?
date: 09-02-2015
published: true
publish_date: 09-02-2015
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 ! Note! Since “BOA-2.4.0”:https://omega8.cc/boa-240-full-edition-349 the @.dev.@ mode works only for site aliases, no longer for the main site name. We have changed this logic to avoid frequent confusion, because people tend to use @.dev.@ in the main site name and then experience various issues when going with live domain, because the site behavior changes then. To avoid further confusion we have made it so @.dev.@ mode is turned on only when it is used in the site alias, and not in the main site name. When used in the main site name, it behaves exactly as a live site domain, to make your workflow more predictable.

 »It is good to know that BOA still protects all requests to dev-type URLs (including “dev.” with a single dot in front of the site name) from known spiders and search engines indexing, but now you have to make sure that the main site name and all other aliases either don’t have any valid DNS record (but can be mapped in /etc/hosts on your computer), or that it also uses dev-type keyword, even if the dev-mode works only in aliases. For best results, we recommend to use the built-in “Secure Site”:https://www.drupal.org/project/securesite module, though.

 »When creating a site alias to include @.dev.@ be sure to set the “Redirect all domain aliases to” option to “No redirection”. Note that browsers remember redirections even if you will clear all caches in the browser. You need to restart your browser, or use another browser, after you have disabled aliases redirection, to avoid possible confusion.

When working in the development mode with any site hosted on your Aegir instance, you’ll want to work with some of our optimized caching/aggregation systems turned off. There is a very easy to use auto-switch available. Any site you access with “dev.” at the beginning or with “foo.dev.” or “foo.devel.” anywhere in the subdomain alias, will have some caching/aggregation settings, otherwise forced as enabled, available to turn them off/on manually. It is an important difference, because some people believe that the magic “dev.” or “foo.dev.” or “foo.devel.” switch in the subdomain will simply force all caches to be disabled, which is not the case. Note also that there must be a dot *after * the dev or devel keyword, thus URLs like dev-foo.com will not work, while bar.dev.foo.com or dev.foo.com will work.

When you access any site via proper dev alias, some (as listed below) settings on the performance page will be no longer hardcoded, so you can turn them on/off as you wish – but remember – it will be then turned on/off depending on your choice only when you access the site with the proper dev subdomain, while all visits to non-dev URLs will still experience hardcoded caching/aggregation.

Which performance related settings are disabled automatically by default then, and why? Are there any exceptions or workarounds available?

Let’s start with important note: the dev switch will lower “Speed Booster”:http://omega8.cc/speed-booster-redis-boost-and-advagg-108#speed system cache TTL from the default 10 to just 1 second (for non-bots visitors only, since it leverages extra cookie, and bots typically don’t accept cookies), but will *not * disable it completely for security reasons. Still, 1 second cache TTL effectively disables it, since you probably don’t click on the same URL several times a second. The dev switch will *not * disable “Redis”:http://omega8.cc/speed-booster-redis-boost-and-advagg-108#cache integration. It is because disabling Redis would cause inconsistent results and make development difficult. Please check the hints further below to learn how to disable both Redis and Speed Booster completely for debugging. Here is a full list of all typical settings on the /admin /settings /performance page in D6 and /admin /config /development /performance page in D7 and their defined behaviour.

`D6 Caching Mode`: Forced as Normal unless proper dev alias is used  
`D6 Minimum Cache Lifetime`: Forced as none unless Redis is disabled  
`D6 Page Cache Maximum Age`: Forced as none unless Redis is disabled  
`D6 Page Compression`: Always Forced as Disabled – Nginx does that already  
`D6 Block Cache`: Never Forced  
`D6 Optimize CSS Files`: Forced Enabled or Forced Disabled if AdvAgg is present  
`D6 Optimize Javascript Files`: Forced Enabled or Forced Disabled if AdvAgg is present

`D7 Cache Pages For Anonymous Users`: Forced as Enabled unless proper dev alias is used  
`D7 Minimum Cache Lifetime`: Forced as none unless Redis is disabled  
`D7 Expiration Of Cached Pages`: Forced as none unless Redis is disabled  
`D7 Compress Cached Pages`: Always Forced as Disabled – Nginx does that already  
`D7 Aggregate And Compress CSS Files`: Forced Enabled unless proper dev alias is used  
`D7 Aggregate Javascript Files`: Forced Enabled unless proper dev alias is used

Note that some settings change their behaviour depending on the proper dev keyword present in the subdomain, while other are affected only when Redis is disabled or AdvAgg module present.

It is good to know that you don’t need to rename the site to be able to work on it in the dev mode. Simply “add an extra domain alias”:http://omega8.cc/how-to-manage-aliases-and-redirects-127 with “dev.” at the beginning or with “foo.dev.” or “foo.devel.” anywhere and use it to access the site, when you wish to skip some otherwise hardcoded caching or aggregation settings.

<a name="debug-a"></a>

1Hint: If you really need to disable CSS or JS aggregation also on non-dev URLs until you will fix your theme or module to make it aggregation friendly, you can “temporarily add”:http://omega8.cc/how-to-edit-settingsphp-file-230 to your `local.settings.php` file two lines: `unset($conf['preprocess_css']);` and `unset($conf['preprocess_js']);` – this will allow you to disable and enable CSS and JS aggregation in the site configuration (the performance admin page mentioned above). Please remember that *disabling aggregation permanently is not allowed * in our hosted environment.

<a name="debug-b"></a>

2Hint: To disable on the fly either Redis or Speed Booster and Boost on any URL (also without proper dev keyword in the URL) please append `?noredis=1` (for Redis) and/or `?nocache=1` (for Speed Booster and Boost) to the end of the URL.

<a name="debug-c"></a>

3Hint: To disable Redis integration temporarily for debugging, either per site or per platform, you can set @redis_cache_disable = TRUE@ in either “site or platform level INI file”:https://omega8.cc/how-to-control-boa-on-site-and-platform-level-293. Please remember that *disabling Redis permanently is not allowed * in our hosted environment, unless individually accepted by our support staff for important reasons.

<a name="debug-d"></a>

4Hint: To force lower than default Speed Booster cache TTL you could “add one extra line”:http://omega8.cc/how-to-edit-settingsphp-file-230 in the `local.settings.php` file: `header('X-Accel-Expires: 1');` and if there are still issues to debug, you could disable Speed Booster completely with this line: `header('X-Accel-Expires: 0');` – but please remember that *disabling Speed Booster permanently is not allowed * in our hosted environment.