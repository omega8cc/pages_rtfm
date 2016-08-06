---
title: How to Export Your Site From Aegir?
slug: how-to-export-your-site-from-aegir-241
menu: How to Export Your Site From Aegir?
date: 04-08-2014
published: true
publish_date: 04-08-2014
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

You can export any of your Drupal sites from our Hosted Aegir environment onto any other host, to another Aegir system or as a standalone Drupal site, using the steps outlined below. To export your site, you will need three separate “pieces”:

# A database dump, saved in the database.sql file  
 # Everything from the @sites/foo.com/@ directory  
 #  The complete “platform”:platform codebase underneath this site

1a Log into the Aegir control panel and run the “Backup” task on your site. This will create a single, compressed archive in your account @~/backups/@ directory. This archive includes the database dump and a complete @sites/foo.com/@ directory. This method is good when the site’s files directory is smaller than 1 GB in total. For bigger sites you should use method 1b.

1b You can export the site’s database only, with command shown below to avoid running the heavy Backup task in Aegir, and then copy @sites/foo.com/@ directory separately, for example with @rsync@ fast method over SSH. Note that you could run this @sql-dump@ magic command also remotely from your new server. Here is the full command:

  
`$ ssh <strong>user.ftp@host.ip</strong> 'drush @foo.com sql-dump' > dump.sql`

 * Replace @user.ftp@ with your SSH/FTPS account username.  
 * Replace @host.ip@ with the domain where you log into Aegir control panel.

2 Copy this archive file to your local drive if you can’t transfer the database and all site’s files directly between servers. You can use SFTP or FTPS. Or, with @rsync@ over SSH available also on the new server, you can copy directly to another server where the site will be hosted.

3 Copy the platform directories and files. If you’ve been using your own “custom platform”:custom-platform, you have full access to all the files, so you can copy them easily. With our “built-in platforms”:built-in-platforms, the best method is to use the @rsync@ command. Here is the full command:

  
`$ rsync -avzuL -e ssh <strong>user.ftp@host.ip:/path/to/platform /local/path/</strong>`

! This command relies on the @-L@ option, so make sure you get those options correct. You must replace the bold *placeholders * with your real account credentials:

 * Replace @user.ftp@ with your SSH/FTPS account username.  
 * Replace @host.ip@ with the domain where you log into Aegir control panel.  
 * Use full system paths (see below).

 With both the Aegir backup archive from @~/backups/@ or the database dump file and @sites/foo.com/@ directory, plus the complete platform files, you can “import your Drupal site into any other Aegir instance”:import. You can also rebuild it as a standalone Drupal site.

! *Help! “rsync” Copies All the Other Sites! * If you copy a platform with that @rsync@ command, you will copy the files of other sites. To avoid this, use the @–exclude@ option for @rsync@ for every site name you don’t want to copy, for example: @–exclude=sites/bar –exclude=sites/other@

! *Don’t Use Symlinks in the Path to the Platform*. When copying the platform with the @rsync@ command, you’ll need to use the full system paths. Don’t use relative symlinks that begin with @~/platforms@ or @~/clients@ or @~/static@. You can find the full path in any of these ways:

 * Log into Aegir and check the platform node. This page will include the full path to the platform.  
 * SSH in and type `'drush @foo.com dd'`. It will show the full path you are looking for.

[platform]https://omega8.cc/what-is-a-drupal-platform-on-aegir-244  
 [custom-platform]https://omega8.cc/how-to-add-custom-platform-properly-140  
 [built-in-platforms]https://omega8.cc/platforms  
 [import]https://omega8.cc/import-your-sites-to-aegir-in-8-easy-steps-109