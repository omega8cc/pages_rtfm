---
# http://learn.getgrav.org/content/headers
title: BOA-2.0.2 Edition
slug: boa-202-edition-147
menu: BOA-2.0.2 Edition
date: 09-02-2012
published: true
publish_date: 09-02-2012
# unpublish_date: 09-02-2012
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.0.2 – this Big Edition includes many new features, five new platforms, eight updated platforms, new Drupal core versions and many fixes and improvements introduced in the last six weeks since previous Edition.

 
    ### Stable Edition BOA-2.0.2
    ### Date: Thu Feb 9 14:00:00 EST 2012
    ### Installs Aegir 2.0.2
    
    # Note on new and updated platforms and new Drupal core:
    
      All 6.x and 7.x platforms have been updated with latest core,
      so they are all in fact new in this BOA Edition, but we list here
      only really new platforms or those with new version released
      since last BOA Edition, with one exception: we list also basic
      6.24.1 and 7.12 platforms as new.
    
      Please note that instead of waiting for 6.25, we already
      included patches required to fix major issues with 6.24:
    
      http://drupal.org/node/1425868
      http://drupal.org/node/1425260
    
      Our Pressflow 6.24.1 +Extra version includes not only listed
      above patches, but also a few extra, performance related
      patches discussed here:
    
      http://groups.drupal.org/node/187209
    
      Note also that we renamed too basic Acquia 7.x platform to
      Ubercart 3.x platform. It is based on the same acquia install
      profile, but includes all contrib modules required for any
      basic Ubercart 3.x site.
    
      NOTE: before you will try to upgrade any of your sites,
      please read our important how-to:
    
      http://omega8.cc/the-best-recipes-for-disaster-139
      http://omega8.cc/are-there-any-specific-good-habits-to-learn-116
      http://omega8.cc/managing-your-code-in-the-aegir-style-110
    
      REALLY, PLEASE READ IT TO AVOID SOME HEAVY HEADACHES!
    
    # New Octopus platforms:
    
      Drupal 7.12 ------------------ http://drupal.org/drupal-7.12
      NodeStream 2.0-alpha6 -------- http://nodestream.org
      OpenPublish 3-alpha3 --------- http://openpublishapp.com
      Pressflow 6.24.1 ------------- http://pressflow.org
      Ubercart 3.0.1 --------------- http://ubercart.org
    
    # Updated Octopus platforms:
    
      Acquia Commons 2.4 ----------- http://acquia.com/drupalcommons
      Commerce Kickstart 1.3 ------- http://drupalcommerce.org
      ELMS 1.0-alpha6 -------------- http://elms.psu.edu
      Open Atrium 1.2.1 ------------ http://openatrium.com
      Open Deals 1.0-beta7 --------- http://opendealsapp.com
      Open Outreach 1.0-beta7a ----- http://openoutreach.org
      ProsePoint 0.43 -------------- http://prosepoint.org
      Videola 1.0-alpha2 ----------- http://videola.tv
    
    # New features:
    
      * Barracuda now supports Debian Lenny to Squeeze major upgrade.
        Of course you should create full backup image before running
        this major system upgrade, just in case, but all the rest
        is fully automated - it is enough to set advanced configuration
        option in Barracuda to _LENNY_TO_SQUEEZE=YES and run Barracuda
        as usual. It will upgrade your system to Squeeze and re-build
        everything, with almost no downtime during the upgrade.
        You will still need to reboot the server when it will complete
        all upgrades.
    
        Important: Debian Lenny reached EOL on February 6, 2012.
        Details: http://lists.debian.org/debian-announce/2012/msg00001.html
    
      * All new 7.x sites now run on latest PHP-FPM 5.3.10 by default.
        For existing sites it is enough to re-verify them in your
        Aegir control panel to get them on PHP-FPM 5.3.10 automatically.
    
        All existing and new 5.x sites run on the old PHP-FPM 5.2.17
        version by default and you can't change that.
    
        You can still choose between PHP-FPM 5.2.17 and 5.3.10 for
        all your 6.x sites - just let us know via http://omega8.cc/support
        that you wish to switch to 5.3.10 - but make sure first that all
        your 6.x sites are fully PHP 5.3 compatible. By default all
        6.x sites still run on PHP-FPM 5.2.17.
    
        Of course you could choose 5.3.10 for 6.x sites on one Octopus
        instance and 5.2.17 on another - on the same server. Just one more
        reason to use Octopus built-in intelligence :)
    
        All of this works the same both for Aegir Master Instance
        and all Aegir Satellite Instances.
    
      * Both Speed Booster, Boost and Redis/Memcached supports separate
        caches per mobile device, so it is safe to use separate themes
        or content for mobile devices. We use simple logic to determine
        the kind of device and there are separate cache bins for
        mobile-tablet, mobile-smart and mobile-other.
        You can review it here: http://bit.ly/wYz6PG
    
      * Purge module is now enabled by default in all 6.x and also 7.x
        sites. Now Speed Booster works like a Boost - it expires
        immediately the cache for any node/page as soon as it has been
        edited or comment added. It also automatically expires the cache
        for the homepage and RSS feed at once - but only when the node
        is promoted to the homepage. You no longer need to wait
        up to one hour for Speed Booster cache expiration. Plus, unlike
        in Boost, it purges all separate caches for all mobile devices
        along with non-mobile cache, at once. Now you have a good reason
        to disable Boost and use our crazy fast Speed Booster only.
    
      * You can use GeoIP data provided by your Nginx server
        in your custom code or modules with variables:
        $_SERVER['GEOIP_COUNTRY_CODE'] and $_SERVER['GEOIP_COUNTRY_NAME']
        to display content or block depending on the visitor's country.
        You can check/review it from your location also on command line
        with: 'curl -I http://your-domain' - you will see GeoIP headers.
    
      * You can safely manage Clients/Users attached to hosted sites
        in your Aegir interface. Make sure that all sites have its
        associated Client! Otherwise the site will be listed as available
        for all Clients/Users you have added. The site can lost its
        association with Client after Clone task if there is any
        non-alphanumeric value in the Client name, like &.
    
      * CloudFlare specific header 'CF-Connecting-IP' is now supported
        out of the box and available as standard $_SERVER['REMOTE_ADDR']
        in all 5.x, 6.x and 7.x platforms without any contrib module.
    
      * You can disable both Boost and Speed Booster on the fly
        by adding ?nocache=1 to any URL. Useful for debugging.
    
      * Speed Booster offers now also ESI microcaching, as explained
        in this article: http://groups.drupal.org/node/197478.
        This may enhance not only anonymous visitors, but also
        logged in users experience, since it allows you to separate
        microcache for ESI/SSI includes (valid for just 15 seconds)
        from both default Speed Booster cache for anonymous visitors
        (valid by default for 3 hours, unless purged on demand via
        recently introduced Purge/Expire modules) and also from
        Speed Booster cache per logged in user (valid for 60 seconds).
        The ESI module is included in all 6.x platforms but is not
        enabled and not configured automatically, so please consult
        its documentation for details on how to use it properly.
    
        Now you have three different levels of Speed Booster cache
        to leverage and deliver the 'live content' experience for
        all visitors, and still protect your server from DoS or
        simply high load caused by unexpected high traffic etc.
    
      * Automatic configuration of options required when Barracuda
        detects _VMFAMILY=AWS (Amazon EC2).
    
      * Both _NGINX_WORKERS and _PHP_FPM_WORKERS are now configurable.
    
      * You can avoid overwriting /etc/mysql/my.cnf with empty
        control file: $ touch /etc/mysql/custom.my.cnf
    
      * You can avoid overwriting /opt/etc/php.ini on upgrade
        with empty control file: $ touch /opt/etc/custom.php.ini
    
      * You can avoid overwriting /usr/local/lib/php.ini on upgrade
        with empty control file: $ touch /opt/etc/custom.php.ini
    
      * You can avoid overwriting /opt/local/etc/php53.ini on upgrade
        with empty control file: $ touch /opt/etc/custom.php53.ini
    
      * You can avoid overwriting /var/spool/cron/crontabs/root on upgrade
        by adding your extra/custom entries in the extra file:
        $ nano /var/xdrago/cron/custom.txt
    
      * You can avoid overwriting your CSF configuration on upgrade
        with empty control file: $ touch /var/log/custom.csf.log
    
    # New o_contrib modules:
    
      * taxonomy_edge-6.x-1.3 (with core patch)
      * taxonomy_edge-7.x-1.1 (with core patch)
      * purge-6.x-1.x
      * purge-7.x-1.x
      * expire-6.x-1.x
      * expire-7.x-1.x
    
    # Changes:
    
      * Nginx upgrade to 1.0.12
      * Lshell upgrade to 0.9.15-beta1
      * Percona upgrade to 5.5.19
      * Chive upgrade to 1.0.2
      * Git upgrade to 1.7.9
      * Suhosin upgrade to 0.9.33
      * Textile upgrade to 2.3
      * Mytop is now installed by default.
      * Drush based method for sites cron is more reliable and now set by default.
      * More compact naming for platforms in Octopus.
      * Speed Booster cache per logged in user now valid for only 60 seconds.
      * Speed Booster anonymous cache now valid for 3 hours, unless purged.
      * Extra $_COOKIE[OctopusCacheID] has been removed.
      * We use $cache_uid from parent map (Nginx) in fastcgi_cache_key.
      * Forced external caching only for Pressflow 6 core.
      * Octopus installs by default: D7P D7S D7D D6P D6S D6D OAM.
      * We no longer need to force Percona on Oneiric. MariaDB also works.
      * We no longer need to force MariaDB on Lenny and MariaDB Natty on Oneiric.
      * We no longer need to use Percona for Maverick on Natty and Oneiric.
      * We use _THIS_DB_HOST=localhost by default.
      * Secure/restricted access to manage users/clients is open by default
        in every Aegir Satellite Instance also for the extra non-uid=1 admin.
      * Users in every Aegir Satellite Instance are protected with userprotect
        and protect_critical_users modules.
      * Some default SQL limits have been increased.
      * The insecure D7 plugin manager is now forced as disabled by default.
      * The hosting_platform_pathauto module is now enabled in Aegir by default.
      * The provision_boost module is now added and enabled in Aegir by default.
    
    # Fixes:
    
      * Simplified Nginx config with 'modern', 'octopus' and 'legacy' templates.
      * Removed duplicate code and fixed caching logic for D5, D6 and D7.
      * Fixed logic for ESI microcache and Boost cache.
      * Removed imageinfo_cache module. It breaks platforms with imagecache module.
      * Disable deslash in globalredirect to avoid redirect loop.
      * Load IonCube also in php-cli.
      * Use core version in paths for all platforms.
      * Make sure that 301 redirects are only microcached - 5 seconds by default.
      * Do not run duplicate PHP-FPM rebuild on upgrade when there is
        no new DB server version installed/available.
      * Set boost_ignore_htaccess_warning to 1 by default.
      * Use provision_civicrm 6.x-1.x branch instead of outdated master.
      * Fix for broken regex on lshell.conf update per user.
      * All broken symlinks in the clients directory now deleted daily.
      * All broken symlinks in the lshell user home directory now deleted daily.
      * Avoid breaking Aegir upgrade because of high load.
      * Set correct loglevel for Redis to avoid useless I/O noise.
      * Add curl as allowed command to lshell default config.
      * Use faster download instead of git for Pressflow core.
      * Issue #1432668 - Octopus username should never start with a digit.
      * Issue #1408972 - Make nginx rewrites compatible with audio module.
      * Issue #1428990 - Load memcache in php-cli.
      * Issue #1408200 - AgrCache breaks aggregation and should be removed.
      * Issue #1420758 - Make sure that Nginx config includes are really used
                         on initial Barracuda install.
      * Issue #1418608 - Add --with-xmlrpc in the PHP-FPM build by default.
      * Issue #1396204 - Add GeoIP support in Nginx by default
      * Issue #1394152 - Build PHP-FPM with --enable-calendar by default.
      * Issue #1392498 - Do not overwrite CSF configuration on Barracuda upgrade.
    
    # Recommendations:
    
      * Use _FORCE_GIT_MIRROR=github because it is 10x faster than others.


 You can read full changelog as always at: http://bit.ly/newboa

Enjoy!