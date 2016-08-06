---
# http://learn.getgrav.org/content/headers
title: How to use Drush aliases?
slug: how-to-use-drush-aliases-321
# menu: How to use Drush aliases?
date: 01-08-2014
published: true
publish_date: 01-08-2014
# unpublish_date: 01-08-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

While Aegir manages Drush aliases for its backend needs, they are normally not available for the main nor the extra shell users on the instance. But starting with 2.2.0, BOA automatically manages copies of all Drush aliases, by adding them, updating or removing, every 5 minutes, once it detects that there are changes applied, like: the site has been migrated to another platform, or associated client/owner has been updated.

You no longer need to @’cd’@ to the respective site directory to perform some available Drush tasks. Just check the available aliases list with @’drush aliases’@ and then enjoy the beauty of ‘`drush @foo.com command`‘ syntax. Still, there are things which may work differently. Thanks to those improvements for Drush based workflows which use \_Drush on the server\_, either locally, or remotely over SSH, you can now run (from your desktop or any other server) commands like, for example:

` ssh user.ftp@host.ip 'drush @foo.com sql-dump' > dump.sql`  
` ssh user.ftp@host.ip 'drush @foo.com cc all'`  
` ssh user.ftp@host.ip 'drush @foo.com up'` «– possible, but “\*don’t use it on live sites!\*”:https://omega8.cc/your-drupal-site-upgrade-safe-workflow-298  
` ssh user.ftp@host.ip 'drush @foo.com status'`

Did you know that all Drush commands available in BOA now work also remotely over SSH with aliases? Previously we didn’t support using \_Drush remotely\_, because the limited shell couldn’t securely accept some commands used in Drush behind the scenes and displayed the error “forbidden char/command over SSH”. For example, you had to use two commands shown below instead of single @sql-sync@ command:

` ssh user.ftp@host.ip 'drush @foo.com sql-dump' > dump.sql`  
` drush @foo.com.dev sqlc `

This workaround is no longer required and now you can use @sql-sync@ command as well -- but of course you have to maintain and update both Drush aliases locally. If you will find any Drush command which still triggers "forbidden char/command over SSH" error,  "please submit a bug report on GitHub":https://github.com/omega8cc/boa/issues.

Note that when you prefer two commands listed above over the single @sql-sync@ command, you can manage just the local alias for `@foo.com.dev`, while the alias on the BOA server for `@foo.com` is updated automatically once you migrate the site between platforms, so its db credentials change. As a result, using the two-steps method may become more convenient than the @sql-sync@ shortcut, especially when combined with local shell aliases and SSH keys.