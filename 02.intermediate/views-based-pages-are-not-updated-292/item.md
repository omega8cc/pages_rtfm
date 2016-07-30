---
# http://learn.getgrav.org/content/headers
title: Views based pages are not updated
slug: views-based-pages-are-not-updated-292
# menu: Views based pages are not updated
date: 06-11-2013
published: true
publish_date: 06-11-2013
# unpublish_date: 06-11-2013
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

<a name="debug-q"></a>

QMy homepage and other Views based pages are not updated properly with new or updated content, even if Speed Booster cache is left at default 10 seconds. Is there any hidden setting to make these pages “live” and avoid displaying outdated, cached results?

<a name="debug-a"></a>

AIt could be related to Views specific caching which populated Redis cache (not Speed Booster cache) with longer than expected cache TTL (time-to-live) value. You can verify if this is the case by adding `?noredis=1` to the visited URL. If you see fresh content now, it is because Redis, which has views cache entries stored with longer than expected TTL is now disabled on the fly. But it is not Redis fault. There is now built-in “Views cache bully”:https://drupal.org/project/views\_cache\_bully module enabled by default in all your sites, which forces 1h cache TTL on all views without any caching configured yet. It does a good job with auto-enabling caching where needed. Of course it is not ideal and could be improved. If you have set your own caching settings in all your views, “Views cache bully”:https://drupal.org/project/views\_cache\_bully will not alter them.

<a name="debug-b"></a>

»If you still experience issues after configuring your own caching settings properly in your views, please try to disable “Views cache bully”:https://drupal.org/project/views\_cache\_bully module and also set to TRUE related variable: `views_cache_bully_dont_enable = TRUE` in this site platform specific INI file: `boa_platform_control.ini` located in the `/sites /all /modules` directory. If there is only `default` template file there, please copy it as `boa_platform_control.ini` in the same directory and edit the line for `views_cache_bully_dont_enable` variable. You will find extensive built-in docs there as well.

<a name="debug-c"></a>

»Note: there are two (2) views / cache related modules auto enabled: “Views cache bully”:https://drupal.org/project/views\_cache\_bully and “Views content cache”:https://drupal.org/project/views\_content\_cache, so it is also possible that the problem / conflict is not caused by “Views cache bully”:https://drupal.org/project/views\_cache\_bully, but by “Views content cache”:https://drupal.org/project/views\_content\_cache, even if it would be an extremely edge case, so it is a good idea to check this as well. Besides, “Views cache bully”:https://drupal.org/project/views\_cache\_bully doesn’t affect any view with already enabled own caching — either simple or with the help of more advanced “Views content cache”:https://drupal.org/project/views\_content\_cache. It only affects views with no caching enabled at all (and there should be no such views in any live site, hence its name and the idea behind). That said, we are eager to investigate all edge cases reported so we could improve both our configuration defaults and included / enabled modules code, so “please share with us”:https://omega8.cc/support any findings, if possible.

<a name="debug-d"></a>

!Please remember that no caching enabled in views is considered as a serious bug and a common source of performance degradation for any live site and as such is not allowed on our hosted services, which are designed to provide the best, high performance Drupal hosting on the planet. The only exception is when you have some view(s) which can’t use any caching, for example to not break Views based checkout, like it is known to work in the Commerce module. BOA daily maintenance agent will automatically disable “Views cache bully”:https://drupal.org/project/views\_cache\_bully if it detects that Commerce or Ubercart is enabled.