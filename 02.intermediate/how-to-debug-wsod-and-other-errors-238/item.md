---
# http://learn.getgrav.org/content/headers
title: How to debug WSOD and other errors?
slug: how-to-debug-wsod-and-other-errors-238
# menu: How to debug WSOD and other errors?
date: 26-03-2014
published: true
publish_date: 26-03-2014
# unpublish_date: 26-03-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

<a name="debug-q"></a>

QHow to display all PHP errors on screen to debug WSOD (white screen of death), since there is no access to server error logs, at least in the hosted BOA?

<a name="debug-a"></a>

AThere is a very easy to use auto-switch available to make this happen. Any site you access with “dev.” at the beginning or “foo.dev.” or “foo.devel.” anywhere in the subdomain alias, will have all PHP errors enabled and displayed on screen, on the fly, so you can easily check the reasons behind PHP errors, including those causing otherwise complete WSOD, right in your browser. This is why you should keep any dev alias as a top secret, or even better delete it when not needed, as it may expose your site for remote vulnerabilities by displaying too much data in the errors on screen. Sometimes you can experience error 500 or just a WSOD, and there will be no errors displayed on the dev URL – typically it could be either a result of uploading truncated/incomplete PHP file to your module or theme, or (most often) you didn’t clear all caches after some code update, so the error is not really on the PHP level, and rather on the database level because of messed cache tables/records, hence no PHP errors to display. In this case start with clearing all caches either by using “Flush all caches” task in Aegir, or on command line with `drush cc all`. If the problem persists, try also the “Rebuild registry” task. Note that you don’t need to rename the site to be able to work on it in the development mode. Simply “add an extra domain alias”:http://omega8.cc/how-to-manage-aliases-and-redirects-127 with “dev.” at the beginning or with “foo.dev.” or “foo.devel.” anywhere in the alias name and use it to access the site, when you wish to enable error reporting on the screen. Note that there must be a dot \*after * the dev or devel keyword, so URLs like dev-foo.com will not work, while bar.dev.foo.com or dev.foo.com will work. You may also want to check related article: “How to disable all caching and aggregation?”:http://omega8.cc/how-to-disable-all-caching-and-aggregation-115

 ! Note! Since “BOA-2.4.0”:https://omega8.cc/boa-240-full-edition-349 the @.dev.@ mode works only for site aliases, no longer for the main site name. We have changed this logic to avoid frequent confusion, because people tend to use @.dev.@ in the main site name and then experience various issues when going with live domain, because the site behavior changes then. To avoid further confusion we have made it so @.dev.@ mode is turned on only when it is used in the site alias, and not in the main site name. When used in the main site name, it behaves exactly as a live site domain, to make your workflow more predictable.