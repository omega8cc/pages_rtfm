---
# http://learn.getgrav.org/content/headers
title: BOA-2.0.8 Edition
slug: boa-208-edition-255
menu: BOA-2.0.8 Edition
date: 07-04-2013
published: true
publish_date: 07-04-2013
# unpublish_date: 07-04-2013
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.0.8 Edition, which includes 3 updated platforms, one critical fix and a few other fixes and improvements introduced in the last four \*days * since previous Edition. Note that this is just a quick release on top of really big BOA-2.0.6 Edition and following 2.0.7 Edition, to address critical issue for Percona based installs introduced in BOA-2.0.6 and provide more recent versions of some popular Drupal distributions, so you don’t need to wait for these updates another month, which is our current target release cycle. This BOA-2.0.8 Edition comes also with major speed improvements for Octopus install and upgrades – [see the example](https://twitter.com/omega8cc/status/320719684292976642).

 
    ### Stable Edition BOA-2.0.8
    ### Date: Mon Apr  8 01:41:36 CEST 2013
    ### Installs Aegir 2.x
    
    # Updated Octopus platforms:
    
      ### Drupal 7.22.1
    
      Commerce 2.6 ----------------- http://drupal.org/project/commerce_kickstart
      NodeStream 2.0-rc5 ----------- http://drupal.org/project/nodestream
      Open Deals 1.19 -------------- http://drupal.org/project/opendeals
    
      All other not listed above platforms are available with latest
      D6 or D7 core, even if there were no new distro version released.
    
    # Fixes:
    
      * Critical Issue #1962690 - Fix for broken Percona support.
    
      * Allow to use [a-z0-9] subdomains and not only [www] for IDN domain names.
      * Change the interval between platforms builds from 5 to 3 seconds.
      * Forced 1s Speed Booster TTL for vhosts behind local proxy is deprecated.
      * Move old firewall logs to backups to avoid crazy load after upgrade.
      * Nginx: Better exceptions handling in the Abuse Guard for js/shs modules.
      * PHP: CLI is at 5.3 since BOA-2.0.4, so symlink old 5.2 binary path to 5.3
      * Update _LENNY_TO_SQUEEZE major upgrade procedure.
      * Update contrib with login_security-7.x-1.2
      * Use static downloads for all distros in stable edition.


 You can read full changelog as always at: http://bit.ly/newboa

Enjoy!