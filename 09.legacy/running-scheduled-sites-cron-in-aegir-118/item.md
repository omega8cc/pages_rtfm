---
# http://learn.getgrav.org/content/headers
title: Running scheduled sites cron in Aegir
slug: running-scheduled-sites-cron-in-aegir-118
# menu: Running scheduled sites cron in Aegir
date: 21-07-2015
published: true
publish_date: 21-07-2015
# unpublish_date: 21-07-2015
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="cron-q"></a>

QHow to run scheduled cron for sites hosted in the Aegir system and is it still possible to run cron manually or maybe remotely, when needed?

<a name="cron-a"></a>

AAegir system manages scheduled cron for all your sites, and runs it by default every 24 hours via standard local @curl@ request to the @/cron.php@ URL. However, there is no remote access to this URL, for security and performance reasons. You can configure (or even disable) cron interval per site by editing site’s node in your Aegir control panel. While the minimum cron interval available for per-site configuration is just 5 minutes, the cron will run with effective 5-15 minutes minimal interval, so the 5 minutes means in practice: as soon as possible. Also all other available intervals will be run with 5-15 minutes precision, depending on the number of sites you host and current load on the system. Your Aegir instance will not run scheduled cron for sites when there is too high load on the system temporarily, typically during daily system backups, and during nightly (server timezone) database servers backups, for up to 1 hour window.

<a name="cron-w"></a>

»Our customized, @curl@ based method with protected access to @/cron.php@ will work even if the main site domain name doesn’t point to your instance IP address yet or when you are using third-party proxy like CloudFlare. Just another kind of BOA magic!

<a name="cron-w"></a>

»You can also run cron on demand in the site admin area (using some working domain alias), or with Drush on command line. If you have “Elysia Cron”:http://drupal.org/project/elysia\_cron configured in any site, you should run @’drush elysia-cron’@ command instead.

<a name="cron-w"></a>

»Please note that cron is automatically disabled for sites with special keywords in the main site name: @dev.@, @devel.@, @tmp.@, @temp.@, @temporary.@, @test.@, @testing.@ — in this case Aegir will still attempt to run cron (if enabled) and report it as “running”, but such requests will be ignored with forced 404 response, so the only way to run cron on sites using listed keywords in their name is to run it manually via site admin area or Drush.

<a name="cron-w"></a>

!The site cron will not work if your site’s DNS is pointed to CloudFlare and not to your instance default IP address or dedicated SSL enabled IP \*and * you have enabled alias redirect in Aegir which points to an alias and not to the site main name defined in Aegir. It is because BOA cron issues local HTTP request to @/cron.php@ with site name via HTTP header pointing to the localhost, thus it works even if the site name doesn’t have a valid DNS at all. But if you have redirect to an alias, which in turn points to some external IP address, like it is with CloudFlare, it will result with @/cron.php@ request going via an alien IP address, which will hit Nginx 403 error, because BOA allows only local @/cron.php@ requests, for security and performance reasons. Disable the redirect, remove the alias used as target and rename the site with Migrate task to use the target name as its main name to fix the problem.

<a name="cron-w"></a>

»Please note that web based cron used in BOA by default will not work if you have made the site protected with extra HTTP Auth layer (typically with included @securesite@ module) and you have not whitelisted @/cron.php@ requests.

<a name="cron-w"></a>

»If none of above edge case exceptions apply and cron still doesn’t work, but is reported as running in Aegir, something else is probably broken or breaks the cron. Try to run the cron with Drush on command line and watch for possible errors and hints to debug this further.