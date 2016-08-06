---
title: Could not back up sites directory for drupal
slug: could-not-back-up-sites-directory-for-drupal-367
menu: Could not back up sites directory for drupal
date: 21-10-2015
published: true
publish_date: 21-10-2015
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="debug-q"></a>

QAll attempts to run Clone or Migrate task in Aegir fail with mysterious error “Could not back up sites directory for drupal.” Why it affects only one of my sites?

<a name="debug-a"></a>

APlease move away the @.sass-cache@ sub-directory, if exists, from theme directory in the affected site. You may need to do it via SSH, since _dot directories_ are by default hidden in FTPS and SFTP, unless you will make them visible in your FTPS or SFTP client. It is normally not needed to remove _dot directories_. The @.sass-cache@ can sometimes cause problems, especially if there were changes and you can’t wait for the nightly permissions fix procedure. Incorrect permissions inside @.sass-cache@ can cause problems for @tar@, which results with non-clean output and breaks the task. The backup sub-task previously would continue anyway, which often resulted with migration broken too late. Now Aegir better detects such issues and fails early. The recommended solution is to avoid site specific space for your code and themes, and always use @/sites/all/@ space, if possible. For more details please read  “The best recipes for disaster”:http://omega8.cc/the-best-recipes-for-disaster-139,  especially Recipe #4 there.

<a name="debug-b"></a>

»What if you don’t have any @.sass-cache@ directory? There can be still some other _dot directories_, like @.git@ or even some _tmp_ files in the site’s files directory which break the tar archive and subsequently also the Drush task. It is a good idea to either remove them, or move elsewhere before running Migration in Aegir again.