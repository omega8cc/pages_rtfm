---
# http://learn.getgrav.org/content/headers
title: Special BOA-1.4S Edition
slug: special-boa-14s-edition-144
# menu: Special BOA-1.4S Edition
date: 24-10-2011
published: true
publish_date: 24-10-2011
# unpublish_date: 24-10-2011
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

The Omega8.cc team is happy to release Barracuda/Octopus Special Edition BOA-1.4S. This Edition includes many new features, seven updated platforms and many fixes and improvements introduced in the last seven weeks since previous Edition.

### Updated Octopus platforms

 * Acquia 7.8.7  
 * Acquia Commons 2.2  
 * CiviCRM 3.4.7  
 * CiviCRM 4.0.7  
 * Commerce Kickstart 1.0-rc4  
 * OpenPublic 1.0-beta3 7.8  
 * Ubercart 2.7 6.22

### New features

 * Mobile devices detection for mobile-tablet, mobile-smart and mobile-other.  
 * Mobile devices detection integrated with Redis/Memcached caches.  
 * Mobile devices detection integrated with Boost cache.  
 * Mobile devices detection integrated with Speed Booster cache.  
 * Responsive Images 7.x module support.  
 * New .barracuda.cnf and .octopus.cnf files for better configuration management.  
 * Ubuntu Oneiric 11.10 is now fully supported.  
 * Issue #1266912 – Support for Apache Solr Attachments – Tika.  
 * Issue #1310082 – Disable XML Sitemap for dev automatically.  
 * Support for fbconnect module.  
 * Support testing->minimal->standard migrations for D7 out-of-the-box.  
 * The Speed Booster $key\_uri enhanced logic included in the default Nginx config.

### Changes

 * Nginx upgrade to 1.0.8  
 * Create mobile cache separate subdirs for Boost by default.  
 * \_MODULES\_ON and \_MODULES\_OFF now forced also for D7 sites.  
 * Do not force hosting\_ignore\_default\_profiles by default.  
 * Some o\_contrib modules received updates – use \_O\_CONTRIB\_UP=YES to apply them.  
 * Allow ‘contrib’ subdirectory in the modules path for allowed PHP files.  
 * Issue #1309996 – Extended support for common modules locations/paths.  
 * Issue #1305542 – Do not overwrite php.ini and my.cnf if control files exist.  
 * Add collectd to the auto-healing monitor and automated restart.  
 * Disable l10n\_update module by default to avoid issues when d.o servers are down.  
 * Updated docs/SOLR.txt to explain how to configure any core to support 7.x.  
 * Duplicate parts of Nginx config moved to maps in the parent server.tpl.php file.  
 * Add ‘drush pmi’ to the list of displayed/allowed commands.  
 * Issue #1243068 – Allow to override in override.global.inc also Redis/Memcached etc.  
 * Deny known crawlers on the HTTPS proxy level.

### Fixes

 * The wkhtmltopdf binary should be always executable if exists.  
 * Issue #1238200 – Use custom \_SSH\_PORT only in TCP\_IN.  
 * Make sure the keys for MariaDB or Percona are added to avoid broken install.  
 * Issue #1307664 – Test repo.percona.com and ftp.osuosl.org availability.  
 * Issue #1262988 – Missing upload\_progress\_test.conf breaks upgrade for older installs.  
 * Issue #1281896 – Add some missing video types to mime.types in the Nginx config.  
 * Do not use path\_alias\_cache in the Hostmaster site to avoid broken URL aliases.  
 * Issue #1270724 and #1263124 – really use /tmp directory during ‘drush dl module’.  
 * Do not break admin/reports/status/rebuild URL in D7.

You can read full changelog as always at: http://bit.ly/newboa

Enjoy!