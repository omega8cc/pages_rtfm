---
# http://learn.getgrav.org/content/headers
title: BOA-2.2.1 Full Edition
slug: boa-221-full-edition-305
# menu: BOA-2.2.1 Full Edition
date: 01-04-2014
published: true
publish_date: 01-04-2014
# unpublish_date: 01-04-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

 We are happy to release BOA-2.2.1 Full Edition, which includes only bug fixes to address a few issues discovered after recent major BOA-2.2.0 Release.

 
    ### Stable BOA-2.2.1 Release - Full Edition
    ### Date: Tue Apr  1 10:28:45 SGT 2014
    ### Includes Aegir 2.x-boa-custom version.
    
    # Release Notes:
    
      This is a bug-fix only release to address issues discovered after recent
      major BOA-2.2.0 Release.
    
    # Fixes in this release:
    
      * Chive Authentication via SSH session doesn't work on some older instances.
      * Compass Tools don't use correct paths to Ruby 2.1.1
      * Cron for sites doesn't work on old instances without Nginx wildcard vhost.
      * FTPS (FTP over SSL) connections may experience TLS problems.
      * PHP: Disabled 'assert' may cause warnings on features revert.
      * PHP: Disabled 'create_function' may break some contrib modules or code.
      * The 'git pull' command is broken in limited shell.
      * The 'rsync' command is broken in limited shell.
      * The 'drush dl foo' command can't be run outside of site directory.
    
    # Known Issues on systems upgraded to BOA-2.2.1 (and 2.2.0) releases
    
      ==> Updated on Tue Apr  8 01:26:47 PDT 2014
    
      @=> Issues fixed in BOA head (running the hotfix in stable is enough):
    
      * Chive Authentication via SSH session may break Nginx due to race conditions.
      * Drush specific dt() wrapper is required in Provision for custom platforms.
      * Issue #2229715 - Tasks queue doesn't work on the Master Instance.
      * PHP: max_input_time should be set to 180 and not 60, by default.
      * The 'scp' command is broken in limited shell.
      * Too broad whitelisting breaks commands in limited shell with 'tmp' keyword.
      * Too restrictive open_basedir defaults break access to valid Tika paths.
      * Zend OPcache directive opcache.enable=1 must be set in all php.ini files.
    
      To fix all those problems you can run as root on self-hosted system:
    
      $ wget -q -U iCab http://files.aegir.cc/update/boa221fix.txt
      $ bash boa221fix.txt
    
      We have fixed this on all hosted and remotely managed Aegir instances already.
    
      @=> Other issues fixed in BOA head (run 'barracuda up-head system' to apply):
    
      * PHP: New Relic extension not installed even if _NEWRELIC_KEY is not empty.
      * Too restrictive open_basedir defaults break access to valid PEAR paths.
    


 You can read the full changelog as always at: http://bit.ly/newboa

Enjoy!