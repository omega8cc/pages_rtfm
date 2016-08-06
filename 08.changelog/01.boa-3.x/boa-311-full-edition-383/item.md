---
# http://learn.getgrav.org/content/headers
title: BOA-3.1.1 Full Edition
slug: boa-311-full-edition-383
menu: BOA-3.1.1 Full Edition
date: 22-06-2016
published: true
publish_date: 22-06-2016
# unpublish_date: 22-06-2016
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /boa-311-full-edition-383
---

We are happy to release BOA-3.1.1 Full Edition, with system security upgrades, improvements and bug fixes, plus all supported Drupal platforms updated to latest versions. Enjoy!

 ```
      ### Stable BOA-3.1.1 Release - Full Edition
      ### Date: Wed Jun 22 12:24:17 PDT 2016
      ### Milestone URL: https://github.com/omega8cc/boa/milestones/3.1.1
      ### Latest hotfix added on: Fri Jun 24 06:01:07 PDT 2016

      # Release Notes:

        This BOA release provides system security upgrades, improvements
        and bug fixes, plus all supported Drupal platforms updated to latest
        versions, and supplied with latest Drupal 7 core (security release).

      # New features and enhancements:

        * Add _SSH_ARMOUR feature
        * Add strict check for supported virtualization systems
        * Allow to install ImageMagick from sources when _MAGICK_FROM_SOURCES=YES

      # Changes:

        * Deprecate support for old Solr versions <4
        * Switch cluster support to 3.x

      # System upgrades:

        * Drush micro-8-15-06-2016
        * MariaDB 5.5.50
        * Nginx 1.11.1
        * PHP 5.5.37
        * PHP 5.6.23
        * PHP 7.0.8
        * Redis 3.2.1

      # Fixes:

        * Add compatibility with magick src
        * Add ToC (Table of Contents) for the Let’s Encrypt section in docs/SSL.txt
        * Downgrade JSmin from 2.0.1 to 2.0.0 -- fixes #993
        * Fix for legacy cluster support
        * Fix for virtualbox detection -- see #972
        * Fix permissions on sites directories
        * Fix sites/all/drush permissions compatibility with Drush 8.2
        * Improve protection for custom solrconfig.xml and schema.xml -- fixes #969
        * Migration: xboa supports only Aegir 2.x -- #960
        * Reinstall default-jre on major OS upgrade, if needed -- fixes #986
        * Remote Drush support regression -- fixes #984
        * The ~/static/control/README.txt is not updated on octopus upgrade #965
        * Update docs/SOLR.txt to match currently supported procedures -- fixes #963
        * Use st_runner() wrapper only for apt-get/aptitude

      # Known problems:

        https://github.com/omega8cc/boa/milestones/3.1.x
```
