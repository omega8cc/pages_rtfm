---
# http://learn.getgrav.org/content/headers
title: BOA-2.2.6 Full Edition
slug: boa-226-full-edition-319
menu: BOA-2.2.6 Full Edition
date: 21-06-2014
published: true
publish_date: 21-06-2014
# unpublish_date: 21-06-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.2.6 Full Edition, which includes great new features, improvements, important changes, many bug fixes, and even 3 new and 7 updated Octopus platforms.

 
    ### Stable BOA-2.2.6 Release - Full Edition
    ### Date: Sat Jun 21 06:14:18 PDT 2014
    ### Includes Aegir 2.x-boa-custom version.
    ### Latest hotfix added on: Mon Jul 14 14:54:04 CDT 2014
    
    # Release Notes:
    
      This release includes great new features, improvements, important changes,
      many bug fixes, plus 3 new and 7 updated Octopus platforms.
    
      IMPORTANT! This is the last Edition in the 2.2.x series, which marks the end
      of Drupal 5, PHP 5.2 and Drush 4 support. Next Edition will open 2.3.x series,
      which will allow us to provide newer Aegir version with built-in Drush 6
      support, sites in subdirectories, and many Aegir User Interface improvements.
    
      If you still host any Drupal 5 sites or you are using PHP 5.2 for D6 sites,
      you will not be able to upgrade to the next 2.3.x Edition and you will have to
      stay on the 'legacy' BOA 2.2.x version, which will receive only system
      security upgrades, but no further feature nor bugfix releases.
    
      This also means that from now on the 'legacy' 2.2.x version will no longer
      receive Drupal core upgrades, even if there will be security core releases.
    
      It is time to upgrade away from Drupal 5 and away from PHP 5.2, if still used.
    
    # New Octopus platforms:
    
      aGov 1.0-rc8 ----------------- https://drupal.org/project/agov
      ERPAL 2.0-b2 ----------------- https://drupal.org/project/erpal
      Restaurant 1.0-a5 ------------ https://drupal.org/project/restaurant
    
    # Updated Octopus platforms:
    
      Commerce 2.15 ---------------- https://drupal.org/project/commerce_kickstart
      Commons 2.18 ----------------- https://drupal.org/project/commons
      Commons 3.14 ----------------- https://drupal.org/project/commons
      Guardr 1.5 ------------------- https://drupal.org/project/guardr
      Open Atrium 2.19 ------------- https://drupal.org/project/openatrium
      Open Outreach 1.7 ------------ https://drupal.org/project/openoutreach
      Panopoly 1.6 ----------------- https://drupal.org/project/panopoly
    
    # New features and enhancements in this release:
    
      * Drush aliases based workflows are now supported also remotely over SSH.
    
        This is significant improvement since we have added automatically generated
        and updated Drush aliases for the on-the-server use in BOA-2.2.0
    
      * Add gems: compass_radix v2 and compass_twitter_bootstrap
      * Add support for automatic Scout App upgrade on RVM/Ruby/Gems upgrade.
      * Install headless JRE and only if Solr is expected to run.
      * Issue #2268889 - Allow to whitelist IPs for chive, cgp and sqlbuddy access.
      * Issues #2248907 #1299526 - Allow to use comments for admin notes.
      * Nginx: Disable proxy_buffering to avoid useless extra layer in local proxy.
      * SQL: Allow to change InnoDB log file size via _INNODB_LOG_FILE_SIZE variable
      * Use better subdirectory tree for Drush extensions.
      * Add support for disable_user_register_protection INI variable on the
        platform level - on self-hosted BOA and Power Engines only.
    
      * Issue #2240277 - Customize Octopus platforms list via control file.
    
        ~/static/control/platforms.info
    
        This file, if exists and contains a single line with supported platforms
        symbols, allows to control/override the value of _PLATFORMS_LIST variable
        normally defined in the /root/.${_USER}.octopus.cnf file, which can't be
        modified by the Aegir instance owner with no system root access.
    
        IMPORTANT: If used, it will replace/override the value defined on initial
        instance install and all previous upgrades. It takes effect on every
        future Octopus instance upgrade, which means that you will miss all newly
        added distributions, if they will not be listed also in this control file.
    
        Supported values which can be written in this file - remember: all in a
        single line, space separated, so not one per line, as listed below
        only for readability:
    
        # D7P D7S D7D --- Drupal 7 prod/stage/dev
        # D6P D6S D6D --- Pressflow 6 p/s/d
        # AGV ----------- aGov
        # CME ----------- Commerce v.2
        # CS7 ----------- Commons 7
        # DCE ----------- Commerce v.1
        # DCS ----------- Commons 6
        # ERP ----------- ERPAL
        # FSR ----------- Feature Server
        # GDR ----------- Guardr
        # MNS ----------- Managing News
        # OA7 ----------- Open Atrium D7
        # OAM ----------- Open Atrium D6
        # OAY ----------- Open Academy
        # OBG ----------- OpenBlog
        # OCH ----------- OpenChurch
        # ODS ----------- Open Deals
        # OOH ----------- Open Outreach
        # OSR ----------- OpenScholar
        # PPY ----------- Panopoly
        # RER ----------- Recruiter
        # RST ----------- Restaurant
        # SRK ----------- Spark
        # TTM ----------- Totem
        # UC7 ----------- Ubercart D7
        # UCT ----------- Ubercart D6
    
        You can also use special keyword 'ALL' to have all available platforms
        installed, including newly added in the future BOA system releases.
    
        Examples:
    
          ALL
          D7P D6P OAM MNS OOH RST
    
      * Issue #314 - Make _BACKEND_ITEMS configurable via _BACKEND_ITEMS_LIST
    
        You can whitelist extra binaries to make them available for web server
        requests, in addition to already whitelisted, known as safe binaries.
    
        NOTE: This feature is available only on self-hosted BOA systems.
    
        Please be aware that you could easily open security holes by whitelisting
        commands which may provide access to otherwise not available parts of
        the system, because the exec() in PHP doesn't respect other limitations
        like open_basedir directive.
    
        You should list only filenames, not full paths, for example:
    
          _BACKEND_ITEMS_LIST="git foo bar"
    
    # Changes in this release:
    
      * Add memcache, memcache_admin to the list of automatically disabled modules.
      * Add support for Debian Squeeze LTS updates.
      * Add support for Debian Squeeze Stable Proposed Updates.
      * Add varnish to the list of automatically disabled modules.
      * Add watchdog_live to the list of automatically disabled modules.
      * Disable and remove not used init scripts on known VM systems.
      * Drush: Upgrade command line version 6 to mini-6-21-06-2014
      * Fast DNS Cache Server (pdnsd) install is no longer optional.
      * Install only vanilla core platforms by default (can be overridden)
      * Nginx: Update default limit_conn settings.
      * Nginx: Use only newer control file to force DoS monitor aggressive mode.
      * Sync permissions with new defaults in the hardened setup.
      * Update files ownership to match defaults in the hardened setup.
      * Use dynamic mirror selection provided by Debian instead of forced static.
    
      * The BOA project has moved to Github!
    
        We no longer use repositories and issue queues on drupal.org, in an effort
        to avoid fragmentation and duplication. We have moved all downloads used
        by Barracuda and Octopus to our mirrors a few months ago, and it helped to
        make BOA faster and more reliable during both system install and upgrades.
    
        The next step is to use http://boa.readthedocs.org as a new home for all
        future documentation efforts - it will build the docs, including printable
        versions, on the fly, using dedicated Github repository as a backend, where
        you can help migrate existing docs and improve them, both via boa-docs
        project issue queue and pull requests:
    
          https://github.com/omega8cc/boa-docs
    
        We also encourage you to use drupal.stackexchange.com for BOA support:
    
          http://drupal.stackexchange.com/questions/tagged/aegir
    
        Please use our Github project for contributing code, reporting bugs,
        and also suggesting new features and ideas:
    
          https://github.com/omega8cc/boa
    
    # System upgrades in this release:
    
      * cURL 7.37.0 (if installed from sources)
      * MariaDB 10.0.12
      * MariaDB 5.5.38
      * MySecureShell 1.33
      * Nginx 1.7.2
      * OpenSSL 1.0.1h (if installed from sources)
      * PHP 5.4.29
      * PHP 5.5.13
      * PHP: Zend OPcache master-28-05-2014
      * Redis 2.8.11
      * Ruby 2.1.2
    
    # Fixes in this release:
    
      * Add caveats to docs/REMOTE.txt
      * Add explicit whitelisting in websh wrapper to avoid any edge case problems.
      * Add info about Two-Factor Auth for Chive in the welcome e-mail template.
      * Add missing exceptions in global.inc and simplify docs/REMOTE.txt
      * Add missing wrapper exceptions required by daily.sh script.
      * Clean up packages cache on finale()
      * Create symlink for boa wrapper on the initial install only.
      * Delete daily both files and directories in the ~/static/trash/
      * Do not remove bundler in CI instances if /root/.keep.bundler.cnf exists.
      * Explain that _ALLOW_UNSUPPORTED works only with head.
      * Fix for _NGINX_DOS_LIMIT logical error in the scan_nginx template.
      * Fix for already installed Open Atrium 2.18 7.28.1
      * Fix for Postfix configuration.
      * Fix incorrect version in the permissions fix.
      * Fix permissions after every upgrade.
      * Fix permissions and owner/group required for feeds (upload) support.
      * Fix regex in procs monitor.
      * Force apticron re-install if apticron.conf is outdated.
      * Generate /data/all/cpuinfo daily to be used in Provision.
      * GPL Ghostscript should be available for the web (PHP-FPM) access.
      * Issue #2248037 - Add Platform and Site INI files Templates on Verify task.
      * Issue #2262935 - Modules dir must be group writable in custom platforms.
      * Issue #315 - Upgrading from older versions of BOA fails
      * Issue #316 - Upgrade fails because of missing cd $_ROOT/.drush/sys line.
      * Issue #319 - XTRAS_LIST settings are being overwritten (Ubuntu)
      * Issue #324 - HTTPS results in redirect loop on AWS due to ignored _MY_OWNIP.
      * PHP: Add protection from switching to not installed CLI or FPM version.
      * PHP: Do not block getenv function.
      * Provision: Use /data/all/cpuinfo generated by BOA daily, if exists.
      * Remove redundant downloads silencer.
      * Remove remote_import if found in the wrong directory.
      * Sanitize logs lines before analyzing them.
      * SQL: Do not run update_innodb_log_file_size() if the size is the same.
      * Sync BOND with BARRACUDA.
      * Update for switch_to_bash procedure.
      * Use already downloaded patches.
      * Use Debian release specific proposed-updates.
      * Use full path to sqlmagic in daily.sh to avoid 'command not found' error.
      * Use static ftp.debian.org instead of unreliable http.debian.net mirrors.
      * Fix for authorized IPs detection in the protected vhosts logic - it should
        ignore serial/remote console logins.
      * Provision: Use higher hardcoded threshold to avoid breaking tasks due to
        high load on multi-CPU systems when provision can't determine the real load.
    


 You can find the full changelog at: https://github.com/omega8cc/boa/blob/master/CHANGELOG.txt

Enjoy!