---
title: BOA-2.2.2 Barracuda Edition
slug: boa-222-barracuda-edition-306
menu: BOA-2.2.2 Barracuda Edition
date: 08-04-2014
published: true
publish_date: 08-04-2014
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

 We are happy to release BOA-2.2.2 Barracuda Edition, which includes only bug fixes to address known security issue with OpenSSL and a few issues discovered after recent major BOA-2.2.0 and BOA-2.2.1 Releases.

 
    ### Stable BOA-2.2.2 Release - Barracuda Edition
    ### Date: Tue Apr  8 07:24:18 PDT 2014
    ### Includes Aegir 2.x-boa-custom version.
    
    # Release Notes:
    
      This is a bug-fix only release to address issues discovered after recent
      major BOA-2.2.0 and subsequent BOA-2.2.1 Releases.
    
      The most important problem fixed in this Release is related to known OpenSSL
      security issue, which has been fixed in OpenSSL 1.0.1g
    
      To learn more please visit: http://heartbleed.com
    
      @=> Note for those on self-hosted BOA (skip this if you are on a hosted Aegir)
    
      We recommend that you enable _SSL_FROM_SOURCES=YES option in your system
      /root/.barracuda.cnf file, to always build latest OpenSSL from sources.
      Note that it will also trigger OpenSSH and cURL install from sources, plus
      subsequent PHP rebuild to include latest SSL libraries.
    
      Note that _SSL_FROM_SOURCES=YES will not force the build from sources on
      Debian Wheezy and Ubuntu Precise, to avoid confirmed conflicts and because
      both OS versions already provide custom, patched OpenSSL packages.
    
      This Release doesn't include any updates to the Octopus installer, so there is
      no point in running full upgrade. It is enough to run the barracuda only,
      system upgrade in the "silent mode" with:
    
      $ screen
      $ barracuda up-stable system
    
      The system will send you an e-mail with results when the upgrade is complete,
      but there will be no upgrade progress displayed in the console. You can watch
      it, if you prefer, with command (DATE/TIME are placeholders for real values):
    
      $ tail -f /var/backups/reports/up/barracuda/DATE/barracuda-up-DATE-TIME.log
    
    # System upgrades in this release:
    
      * Nginx 1.5.13
      * OpenSSL 1.0.1g (if installed from sources)
      * PHP 5.4.27
      * PHP 5.5.11
    
    # Fixes in this release:
    
      * Chive Authentication via SSH session may break Nginx due to race conditions.
      * Drush specific dt() wrapper is required in Provision for custom platforms.
      * Fix Compass Tools support for Omega (gems dependencies via bundle install).
      * Fix default shell for system level cron tasks.
      * Fix for csf firewall compatibility test.
      * Force better health check on protected vhosts on live SSH-auth update.
      * Improved health check for protected vhosts during live SSH-auth update.
      * Issue #2229555 - On fresh boa install link missing durring install.
      * Issue #2229715 - Tasks queue doesn't work on the Master Instance.
      * Issue #2231093 - Add new line before 'UseDNS no' in the sshd_config file.
      * Issue #2235991 - Drush make needs better exceptions in websh wrapper.
      * Issue #294 - New Relic ext not installed even if _NEWRELIC_KEY is not empty.
      * Nginx: Backup and re-create default wildcard SSL cert/key with rsa:4096
      * Nginx: Generate 4096 bit long DH parameters when _NGINX_FORWARD_SECRECY=YES
      * Normalize localhost entry in /etc/hosts to avoid FQDN mapped to 127.0.0.1
      * PHP: Better default workers limits for the ondemand mode.
      * PHP: max_input_time should be set to 180 and not 60, by default.
      * PHP: Zend OPcache directive opcache.enable=1 must be set in all ini files.
      * Reset PATH to avoid RVM overrides after Compass Tools install/upgrade.
      * The 'scp' command is broken in limited shell.
      * Too broad whitelisting breaks commands in limited shell with 'tmp' keyword.
      * Too restrictive open_basedir defaults break access to valid PEAR paths.
      * Too restrictive open_basedir defaults break access to valid Tika paths.
      * Use rsa:4096 by default in self-signed certs for Nginx and FTPS.
    


 You can read the full changelog as always at: http://bit.ly/newboa

Enjoy!