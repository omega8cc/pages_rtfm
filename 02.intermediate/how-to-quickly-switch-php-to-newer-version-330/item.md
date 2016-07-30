---
# http://learn.getgrav.org/content/headers
title: How to quickly switch PHP to newer version?
slug: how-to-quickly-switch-php-to-newer-version-330
# menu: How to quickly switch PHP to newer version?
date: 04-05-2016
published: true
publish_date: 04-05-2016
# unpublish_date: 04-05-2016
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="php-q"></a>

QHow to quickly switch PHP-FPM and PHP-CLI version for all Drupal 7 and Pressflow 6 sites on your Aegir Octopus instance? It is enough to use control files, as explained in the how-to below:

 
    
      ###
    #-### Support for PHP-FPM version switch per Octopus instance (also per site)
      ###
    
      ### ~/static/control/fpm.info
      ###
      ### This file, if exists and contains supported and installed PHP-FPM version,
      ### will be used by running every 2-3 minutes system agent to switch PHP-FPM
      ### version used for serving web requests by this Octopus instance.
      ###
      ### IMPORTANT: If used, it will switch PHP-FPM for all Drupal sites
      ### hosted on the instance, unless multi-fpm.info control file also exists.
      ###
      ### Supported values for single PHP-FPM mode which can be written in this file:
      ###
      ### 7.0
      ### 5.6
      ### 5.5
      ### 5.4
      ### 5.3
      ###
      ### NOTE: There must be only one line and one value (like: 7.0) in this file.
      ### Otherwise it will be ignored.
      ###
      ### It is now possible to make all installed PHP-FPM versions available
      ### simultaneously for sites on the Octopus instance with additional
      ### control file:
      ###
      ### ~/static/control/multi-fpm.info
      ###
      ### This file, if exists, will switch all hosted sites to highest
      ### available PHP-FPM version within the 5.3-5.6 range, with ability
      ### to override PHP-FPM version per site, if the site's name is listed
      ### in this additional control file, as shown below:
      ###
      ### foo.com 7.0
      ### bar.com 5.5
      ### old.com 5.3
      ###
      ### NOTE: Each line in the multi-fpm.info file must start with main site name,
      ### followed by single space, and then the PHP-FPM version to use.
      ###
    
    
      ###
    #-### Support for PHP-CLI version switch per Octopus instance (all sites)
      ###
    
      ### ~/static/control/cli.info
      ###
      ### This file, while similar to fpm.info, if exists and contains supported
      ### and installed PHP version, will be used by running every 2-3 minutes
      ### system agent to switch PHP-CLI version for this Octopus instance, but
      ### it will do this for all hosted sites. There is no option to switch this
      ### or override per site hosted.
      ###
      ### NOTE: While current Aegir version 3.x included in BOA works fine with
      ### latest PHP 7.0, many hosted sites, especially using Pressflow 6 core or
      ### older Drupal 7 core without required patch we have included since 7.43.2,
      ### will not work properly and Aegir tasks run against those sites may fail,
      ### so it's recommended to use PHP-CLI 5.6, unless you have verified that all
      ### sites on the instance support PHP 7.0 without issues.
      ###
      ### Supported values which can be written in this file:
      ###
      ### 7.0
      ### 5.6
      ### 5.5
      ### 5.4
      ### 5.3
      ###
      ### There must be only one line and one value (like: 5.6) in this control file.
      ### Otherwise it will be ignored.
      ###


<a name="php-b"></a>

!IMPORTANT: If you still run PHP version 5.3 or 5.4, you should fix your site’s codebase to make it compatible with at least PHP 5.5 or, even better, PHP 5.6, as fast as you can, because \*these deprecated versions will be removed from our systems * “when BOA-3.3.0 is released”:https://github.com/omega8cc/boa/milestones. We highly recommend to check “Acquia docs on Common issues when upgrading Drupal 6.x and 7.x websites to PHP 5.5 or PHP 5.6”:https://docs.acquia.com/articles/common-issues-when-upgrading-drupal-6x-and-7x-websites-php-55-or-php-56

<a name="php-b"></a>

!Please note that “PHP 5.3 is now officially deprecated”:http://php.net/archive/2014.php#id2014-08-14-1 and will not receive any upgrades nor security fixes, so you should seriously consider switching to PHP \*5.6\*. We run “our own Pressflow 6 based site”:https://omega8.cc on PHP \*5.6 * for many months already, and it works great! Note that there is no point in running PHP 5.5 at this stage, because “PHP 5.5 is already deprecated as well”:http://php.net/supported-versions.php.