---
# http://learn.getgrav.org/content/headers
title: BOA-2.0.7 Edition
slug: boa-207-edition-254
menu: BOA-2.0.7 Edition
date: 04-04-2013
published: true
publish_date: 04-04-2013
# unpublish_date: 04-04-2013
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.0.7 Edition, which includes new Drupal 7 core version for all Drupal 7 based platforms, one updated platform and a few fixes and improvements introduced in the last three \*days * since previous Edition. Since this is just a quick release on top of really big BOA-2.0.6 Edition, we will take this opportunity to document some important changes and new features introduced this week.

 
    ### Stable Edition BOA-2.0.7
    ### Date: Thu Apr  4 00:00:17 EDT 2013
    ### Installs Aegir 2.x
    
    === IMPORTANT CHANGES IN THIS AND PREVIOUS BOA-2.0.6 RELEASE
    
    * We are changing default PHP-FPM version used by all Drupal 6 sites to the
      new PHP-FPM 5.3.23 and deprecate PHP-FPM 5.2.17, which is now used only
      for remaining Drupal 5 sites, if hosted.
    
      We also no longer update/rebuild existing PHP 5.2.17 version.
    
      Note that we have already switched PHP-CLI used by your Aegir backend
      to 5.3 in BOA-2.0.4 Edition.
    
      While we believe that it is already a big time for this safe change, please
      let us know via: http://omega8.cc/support if you still need to use old
      PHP 5.2.17 version for your Drupal 6 sites.
    
    * We have removed Drupal 5 from the list of supported platforms. We don't
      delete previously installed D5 platforms yet, but you should really upgrade
      to Drupal 6 and stop using Drupal 5.
    
    * We have changed control files used to disable Redis cache. Previously it was
      cache/NO.txt and now it is:
    
        sites/all/modules/redis_cache_disable.info (platform-wide)
        sites/foo.com/modules/redis_cache_disable.info (per site)
    
      More details in the updated article at: http://omega8.cc/node/115
    
    * We have changed auto-generated $cookie_domain to use dynamic HTTP_HOST
      as before, but you can still force static SERVER_NAME, which stays the same
      for all domain aliases. This may be useful when you prefer to keep users
      logged in while visiting various sub-sites managed with Domain Access
      module. The control file required to force SERVER_NAME as a base for
      $cookie_domain is:
    
        sites/foo.com/modules/cookie_domain.info
    
    * We have switched from Tomcat to Jetty and we support both Solr 3.6.2 and
      previous Solr 1.4.1 version, while self-hosted instances can even use
      Solr 4.2.0. For more information please read docs/SOLR.txt
      linked on the project page: http://drupal.org/project/barracuda
    
    * All known bots receive 24h Speed Booster cache TTL by default.
    
    
    === NEW FEATURES AND FIXES IN THIS AND PREVIOUS BOA-2.0.6 RELEASE
    
    * We have added extra Drush versions available on command line as drush4,
      drush5 and drush6. Note that Aegir backend still uses Drush 4 by default.
    
    * There is new command line tool: sqlmagic. You can use it to fix database
      dumps which can't be imported because of that "SQL SECURITY DEFINER" using
      mysql user from previous system. To get these DEFINERs removed, type:
    
        sqlmagic fix database.sql
    
      You can also use it to convert any site to/from InnoDB/MyISAM.
      Make sure you are in the correct site directory and then type:
    
        sqlmagic convert to-innodb
        sqlmagic convert to-myisam
    
    * You can force three different cache TTL values for Speed Booster, used only
      for anonymous visitors, with different control files, as explained below.
    
      Note that default cache TTL used in Speed Booster is just 10 seconds for
      both logged in and anonymous visitors, and 24 hours for known bots.
    
      To force 15 minutes cache TTL, use:
        sites/all/modules/nginx_cache_quarter.info (platform-wide)
        sites/foo.com/modules/nginx_cache_quarter.info (per site)
    
      To force 1 hour cache TTL, use:
        sites/all/modules/nginx_cache_hour.info (platform-wide)
        sites/foo.com/modules/nginx_cache_hour.info (per site)
    
      To force 24 hours cache TTL, use:
        sites/all/modules/nginx_cache_day.info (platform-wide)
        sites/foo.com/modules/nginx_cache_day.info (per site)
    
      You should use AdvAgg module to avoid broken CSS/layout when you force
      longer cache TTL in the Speed Booster.
    
    * You can also configure Speed Booster cache TTL in the local.settings.php
      extra config file, which allows you to force completely custom TTL per URL
      with some PHP/regex, and if/else logic, by sending desired individual
      header('X-Accel-Expires: xyx'); - where xyz is a TTL in seconds.
    
    * Redis now supports Fast Lock Backend feature in Drupal 6 and 7, which
      replaces Drupal own, SQL database based lock mechanism, but it is not
      enabled by default. To enable this feature, you would need to create
      an empty control file:
    
        sites/all/modules/redis_lock_enable.info (platform-wide)
        sites/foo.com/modules/redis_lock_enable.info (per site)
    
    * You can easily whitelist your IP on the firewall to avoid being blocked
      because of too many HTTP requests. Sometimes it may happen when there is
      essentially no traffic on the instance besides your requests/pageviews
      and/or when there is more than one person actively working on the same
      server from the same IP address.
    
      To avoid that please log in via SSH (on command line) and keep the session
      active with command like "ping foo.bar.com" - otherwise it will disconnect
      you after 15 minutes of inactivity - and it will whitelist your IP address
      on the fly for as long as you are logged in.
    
      Note that this whitelisting is not a full whitelisting - it just increases
      the allowed HTTP requests treshold to avoid unintended self-blocking, but
      it may still block you temporarily after too many failed SSH or FTPS login
      attempts, or when you flood the server with never cached POST requests etc.
    
      This feature has been suggested by Matt Petrowsky - thanks Matt!
    
    * All important passwords, like for mysql root and Aegir system user are
      re-generated on every upgrade. All self-hosted instances, while by default
      still use standard random passwords, may optionally use _STRONG_PASSWORDS=YES
      (which is default in our hosted service) for even better protection, after
      testing that both "randpass 32 esc" and "randpass 32 alnum" commands produce
      well looking, strong passwords and not a binary garbage, which is a sign of
      probably broken or unreliable system /dev/urandom.
    
    # Updated Octopus platforms:
    
      ### Drupal 7.22.1
    
      Commons 3.2 ------------------ http://drupal.org/project/commons
    
      All other not listed above platforms are available with latest
      D6 or D7 core, even if there were no new distro version released.
    
    # Fixes:
    
      * Create dot dirs and keys if not exist, plus known_hosts for system user.
      * Fix the sqlmagic regex to really convert only expected tables.
      * Issue #1958502 - Add missing symlinks to the new Drush extensions.
      * Issue #1960192 - Fix literal path replacement with sites/$new_url in D7.
      * Issues #1930670 #1958898 #1932616 - Fix for hosting_server_update_6200.
      * Taxonomy Edge update to 7.x-1.7 and 6.x-1.7
      * Update contrib in all D7 platforms to ctools-7.x-1.3 - security upgrade.


 You can read full changelog as always at: http://bit.ly/newboa

Enjoy!