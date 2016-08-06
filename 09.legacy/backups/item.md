---
title: Aegir and remote backups rotation policy
slug: backups
menu: Aegir and remote backups rotation policy
date: 07-02-2015
published: true
publish_date: 07-02-2015
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

Our hosted Aegir service comes with a few backup strategies available. There are backups we manage on our side, for all your files and databases. You can also manage your own backups, either scheduled on your remote computer, or created on demand and downloaded from your Aegir control panel directly.

<a name="backup-a"></a>

AFor all hosted Aegir instances we maintain daily, remote backups. They include all your files and databases. All backups are versioned and rotated daily, so there is always a daily copy/version of all your files from the last 30 days. Your daily databases backups are additionally stored on the same server and rotated weekly, plus archived in your remote backup, so there are always two separate daily copies of all your databases from the last 30 days available.

<a name="backup-b"></a>

BYou can manage your own, scheduled backups by running from cron (on your local computer or another server) custom scripts connecting to your Aegir instance over SSH, with @rsync@ used for files, like in “this example”:https://omega8.cc/how-to-export-any-site-properly-241, and @mysqldump@ over SSH for any database you want to archive, as shown in examples below. You can also run Backup task in your Aegir control panel on any site node and then either download/rsync created archive from the @~/backups@ directory or run the Export task in Aegir and download the archive directly, in the browser.

To download only site level files, use command:  
`rsync -avzuL -e ssh user.ftp@host.ip:/path/to/foo.com /local/path/`

To download complete platform codebase with sites files, use command:  
`rsync -avzuL -e ssh user.ftp@host.ip:/path/to/platform /local/path/`

To download database use db credentials from site’s drushrc.php file and command:  
`ssh user.ftp@host.ip mysqldump -u dbuser -pdbpass dbname > dbname.sql`

To download database you can also use drush command with alias:  
`ssh user.ftp@host.ip 'drush @foo.com sql-dump' > dbname.sql`

<a name="backup-c"></a>

CYour Aegir built-in @~/backups@ directory often includes not only the backup archives of all site’s files and databases created when you run the Backup task, normally used later to perform the Restore task easily. Often there are also many, many duplicate archives created on every Clone or Migrate (and Rename) task. Each compressed archive includes all files from the @sites/foo.com@ directory, plus the site’s database dump (but not the platform level files). Also the Restore task creates hot backup before using the backup archive of your choice, so it all can fill your disk space very quickly with many never needed archives. This is why \*we purge the built-in Aegir @~/backups@ directory daily\*, leaving there archives which are 7 days old (max). As a result, some backups will no longer be available for the Restore task, if they were created more than 7 days ago. We recommend that you download any backups created via Backup task in the Aegir control panel if you prefer to keep them long-term in your own, local backups. Note that the same clean-up applies to any backups created with (not recommended due to regularly introduced bugs) Backup and Migrate module, if used.

<a name="backup-d"></a>

»There is no direct access to remote backups, but we accept restore requests via our “support form”:http://omega8.cc/support. Restore is a free service if used occasionally or paid at “hourly rate $152 USD”:http://bit.ly/ext8hour if requested often and/or requires more than 15 minutes of work. Note that the backups we manage are intended mainly for disaster recovery needs (and hopefully will never be needed), so you shouldn’t rely on this backup when you have mistakenly edited or deleted on the server the only copy of some template/theme file. You will be charged “$152 USD”:http://bit.ly/ext8hour per every such request. You should always maintain local backups for all files you expect to modify, implement proper version control with Git and never ever edit any file on the live site directly, especially when you don’t have any local copy.

<a name="policy"></a>

!\*Note that since you can’t use your Aegir instance disk space as an archive space, any files, archives or backups found in your FTPS/SSH account home directory or in the @~/static@ or any other directory which is not a part of a valid Drupal multisite (Aegir platform) structure, will be deleted automatically once discovered, without any notice, and we will not accept any related backup recovery requests.\*