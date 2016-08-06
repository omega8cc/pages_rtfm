---
# http://learn.getgrav.org/content/headers
title: Speed Booster, Redis, Boost and AdvAgg
slug: speed-booster-redis-boost-and-advagg-108
menu: Speed Booster, Redis, Boost and AdvAgg
date: 10-06-2013
published: true
publish_date: 10-06-2013
# unpublish_date: 10-06-2013
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

It is important to understand how all those performance related modules and systems work to leverage all its power and avoid possible side effects or confusion. We will explain all this performance magic in detail below. You will learn some secrets about [Redis Cache](#cache), [Boost](#boost) and [AdvAgg](#advagg) modules and also the [Speed Booster](#speed) system. We will also discuss [When & How](#hints) to use all those available features. Let’s begin!

<a name="cache"></a>

1\*Redis Cache * – this Drupal module implements Redis server support, and works both for logged in users and not-yet-cached in Boost or Speed Booster, anonymous requests. It caches only most of cache specific tables to lower the load on the database server. This module works both in 6.x (via cache\_backport) and 7.x core based platforms. It is included and active by default. You can skip this cache on any URL on demand by adding `?noredis=1` at the end.

<a name="boost"></a>

2\*Boost * – this Drupal module caches full pages and works only for anonymous visitors. It is supported on the Nginx server configuration level directly, so there is no .htaccess required and used, it works out of the box when the module is enabled. Important: the cache directory required by Boost is already created for you in all platforms installed by default. For custom platforms it is created on the fly, but only if you have enabled Boost in any site created in your custom platform and then you have run Verify site task in Aegir – the order matters. This module is not enabled by default, but is included and ready to use. You can skip its cache on any URL on demand by adding `?nocache=1` at the end.

<a name="speed"></a>

3\*Speed Booster * – this is not a Drupal module, but our system level configuration, Drupal version agnostic, enabled by default. It caches full pages, but both for anonymous visitors and logged in users. It is set to be valid (TTL) for 10 seconds only (hardcoded value), but for known bots the TTL is 24 hours (also hardcoded), but when you access the site via “proper dev alias”:https://omega8.cc/how-to-disable-all-caching-and-aggregation-115, it is “automatically lowered to 1 second”:https://omega8.cc/how-to-disable-all-caching-and-aggregation-115 – with separate cache per user, thus far better than existing AuthCache module (not supported here). It is automatically disabled on the fly for 15 seconds after any POST request (any form submit, also for anonymous visitors) or if you will click on any URL like /user * /admin\*. This system is automatically disabled also for all HTTPS requests. You can skip its cache on any URL, on demand, by adding ?nocache=1 at the end. Speed Booster offers also ESI microcaching, as explained in “this article”:http://groups.drupal.org/node/197478. This may enhance not only anonymous visitors, but also logged in users experience, since it allows you to separate microcache for ESI/SSI includes (valid for just 15 seconds) from both default Speed Booster cache for anonymous visitors and also from Speed Booster cache per logged in user. The ESI module is included in all 6.x and 7.x platforms but is not enabled and not configured automatically, so please consult its documentation for details on how to use it properly. Now you have three different levels of Speed Booster cache to leverage and deliver the ‘live content’ experience for all visitors, and still protect your server from DoS or simply high load caused by unexpected high traffic.

<a name="cache-speed-control"></a>

!Note: You can force custom cache TTL values for Speed Booster, used only for anonymous visitors, with special `speed_booster_anon_cache_ttl` variable set either in the site level INI file `boa_site_control.ini` or platform level `boa_platform_control.ini`. More information “on INI files here”:https://omega8.cc/how-to-control-boa-on-site-and-platform-level-293. You should use AdvAgg module to avoid broken CSS/layout when you force longer cache TTL in the Speed Booster. You can also define completely custom logic in the `local.settings.php` to override system defaults. Learn “how to edit this file here”:https://omega8.cc/how-to-edit-settingsphp-file-230. It is especially useful when you want to force separate caching TTL for logged in users and anonymous visitors on a HTTPS-only site where otherwise this TTL defaults to just 1 second, or when you want to disable Speed Booster on some selected URIs — here are some examples:

 
          /**
           * Custom Speed Booster TTL override, for example to force caching
           * on HTTPS-only site, where otherwise default TTL is just 1 second
           */
          if (isset($_COOKIE[$test_sess_name])) {
            // Custom forced Speed Booster cache for logged in users
            $expire_in_seconds = 300;
          }
          else {
            // Custom forced Speed Booster cache for anonymous visitors
            $expire_in_seconds = 3600;
          }
          header("X-Accel-Expires: " . $expire_in_seconds);


 
          /**
           * Custom Speed Booster TTL override, for example to force no-cache
           * on some selected URLs which need to be excluded to always provide
           * dynamic results.
           */
           if (preg_match("/^\/(?:foo|bar)/", $_SERVER['REQUEST_URI'])) {
             header('X-Accel-Expires: 1'); // This disables Speed Booster
             $conf['cache'] = 0; // This disables page caching on the fly
           }


<a name="mobile"></a>

!Note: Speed Booster supports separate caches per mobile device, so it is safe to use separate themes or content for mobile devices. We use simple logic to determine the kind of device and there are separate cache bins for mobile-tablet, mobile-smart and mobile-other. You can “review it here”:http://bit.ly/wYz6PG

<a name="settings"></a>

!Note: When Speed Booster or Boost module is used, any caching related settings available at the site’s performance admin page are never used, because either Speed Booster or Boost takes precedence over native Drupal caching for anonymous visitors.

<a name="broken-layout"></a>

?Both [Boost](#boost) module and [Speed Booster](#speed) system (when used with long TTL) can suffer from the common “broken layout” issue, caused by Drupal standard core behaviour – it purges all aggregated CSS and JS files on standard cache purge action on the performance admin page (the ‘Clear cached data’ button) or even on certain form sumbit actions, while pages still existing in the cache still reference no longer existing, aggregated CSS and JS files.

<a name="advagg"></a>

4To fight with this common issue, you may want to use excellent “AdvAgg(Excellent AdvAgg Module)”:http://drupal.org/project/advagg module, so aggregated CSS/JS files will not be purged/recreated/renamed, but only rebuilt. To quote this excellent module description: “This is the holy grail of CSS & JS aggregation and optimization. If you want your website to load faster, install this module. If you think flushing your CSS/JS directory on certain submit forms is a dumb idea, you should install this module. If you like the idea of using Google’s CDN for jquery.js, install this module. It also aggregates JS in the footer. JS minification/CSS compression.. you guessed it install this module. Gzip CSS/JS files, yep it does that too! Using a private file system? Use this module and bring back aggregation for improved performance! Wish you could use the same aggregate on different pages, guess what? Install the bundler submodule and watch in awe of how fast your site loads.”

!Note: Your “Aegir”:https://omega8.cc/aegir system is already [AdvAgg](#advagg) ready/pre-configured, and the module is is included (but not enabled) by default in all D6 and D7 platforms. Note that due to its “imagecache-like” behaviour, all requests/page views right after enabling [AdvAgg](#advagg) module will take more time to process, until it will generate enough aggregated files. It is normal, one-time process and later you can use the smart “Flush AdvAgg Cache” button at admin/ settings/ advagg to rebuild only required sub-bundle files instead of purging the cache completely. Important: with [AdvAgg](#advagg) module enabled, you must use that smart “Flush AdvAgg Cache” button after editing any existing CSS or JS file in your theme, since using Drupal native ‘Clear cached data’ button will not affect your aggregated CSS/JS files.