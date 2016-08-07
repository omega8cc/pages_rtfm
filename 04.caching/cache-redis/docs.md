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

Using Redis Caching

h2. What Is Redis Caching?

The "Redis module":redis implements caching in Drupal using the "Redis
backend.":http://redis.io/ This caching works both for logged in users
and for anonymous requests which have not yet been cached with
"Boost":module-boost or "Speed Booster":cache-speed-booster.

This module is included and active by default on all platforms based on 6.x and 7.x core.

h2. Task: How to Disable Redis Caching

You are not allowed to disable Redis caching permanently, but you can disable
Redis temporarily for debugging.

h4. How to Disable Redis on Any URL

You can disable the Redis cache for any URL on the fly by adding
@?noredis=1@ at the end.

For example, to disable Redis caching for @http://foo.com/node/1@, browse
 to: @http://foo.com/node/1?redis=1@

h4. How to Disable Redis Completely (and Temporarily)

To (temporarily) disable Redis for debugging, you can create an empty
control file at a special location.

* To disable Redis for a particular *site*:  @/sites/foo.com/modules/redis_cache_disable.info@

* To disable Redis for the entire *platform*:   @/sites/all/modules/redis_cache_disable.info@

If the @Migrate@ or @Clone@ task in Aegir fails with unexpected errors
for an otherwise working site, we recommend that you temporarily disable Redis,
run the task again, and re-enable Redis afterwards.

If Redis still causes problems, you should leave it disabled and wait
until the next morning, when the Redis cache server is fully restarted.
Then enable Redis again.

Problems may happen when you use the @Migrate@ task to @Rename@ the
site to a different name, and then @Rename@ a separate clone of the
site, such as a dev or staging copy, to the original main domain
name. In the Redis cache, the site name is used as a cache key, so
this situation may confuse both Aegir and the site itself because of
outdated entries in the Redis cache.

Disabling Redis permanently is not allowed in our hosted environment,
unless our "support staff":support gives you an exception.

h2. References

* "How to Disable All Caching":cache-disable-all

* "How to Disable CSS and Javascript Caching":cache-disable-css-js


[redis]https://drupal.org/project/redis
[module-advagg]
[module-boost]
[cache-disable-all]
[cache-disable-css-js]
[cache-speed-booster]
[cache-redis]
[redis]https://drupal.org/project/redis
[import-your-site]
[support]http://omega8.cc/support
