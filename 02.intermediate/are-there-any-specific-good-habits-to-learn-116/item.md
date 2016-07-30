---
# http://learn.getgrav.org/content/headers
title: Are there any specific good habits to learn?
slug: are-there-any-specific-good-habits-to-learn-116
# menu: Are there any specific good habits to learn?
date: 30-12-2012
published: true
publish_date: 30-12-2012
# unpublish_date: 30-12-2012
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

<a name="debug-q"></a>

QHow to avoid issues with files/directories access permissions, breaking later even some Aegir task like site clone/migrate, and how to fix them?

<a name="debug-a"></a>

AWhile most of this is already automated, and permissions even fixed automatically every morning (in your server / datacenter local timezone) by our autonomous maintenance system (but only when there is at least one site in the platform), there are still some things you should be aware of, to make your work easier and avoid headaches. Below we will post updated from time to time list of good habits. Note that when you are using FTPS (FTP over SSL) or SFTP (FTP over SSH) access to upload files, all permissions should be set atomatically for you, on the fly – but only for “modules”, “themes” and “libraries”, while all uploaded subdirectories of the “files” directory still require manual chmod -R 777. Also, some SFTP clients don’t respect default system umask, so you should always check permissions on the uploaded/transferred files and directories. The problem is mostly with files and directories rsync-ed or extracted from archives on command line, or downloaded with Drush.

 * Always chmod -R 775 all modules & themes when uploaded via SSH or Drush – see Hints #1 #4.  
 * Always chmod -R 777 all files uploaded to the sites/domain/files directory – see Hints #1 #4.  
 * Never clone/migrate/restore the site if you didn’t chmod uploaded files/directories first.  
 * Re-Verify the site in Aegir after uploading your modules and themes.  
 * Run Verify task on every site and platform after modules updates.  
 * Run Verify task on site and its platform before running Clone task – see Hint #3.  
 * Run Verify task both on the original and cloned sites again after running Clone – see Hint #3.  
 * Run Verify task on site and both platforms before running Migrate task – see Hint #3.  
 * Use Migrate task to rename the site (domain).

<a name="hint-1"></a>

1Hint: Never attempt to chmod “files”, “modules”, “themes” or “libraries” directories, you should chmod only their sub-directories and files. This is because these parent directories are always owned by your Aegir system user, which is separate from your SSH user, and any attempt to run chmod like `chmod -R sites/domain/files` or `chmod -R sites/domain/modules` will always fail. You should run the chmod with commands like `chmod -R sites/domain/files/*` or `chmod -R sites/domain/modules/*` so it will affect only sub-directories.

<a name="hint-2"></a>

2Hint: You may see some errors like “Operation not permitted” when running recursive chmod command on the “files” directory. This is expected, because your SSH user is not an owner of this directory and files owned/created by the web server, yet, you still can (and should) change permissions as recommended in our how-to above, because it will still set correct permissions for files uploaded by you.

<a name="hint-3"></a>

3Hint: We have automated these steps since “BOA-2.0.3”:http://omega8.cc/boa-203-edition-152, so Aegir will run them automatically for you, however it is still a good idea to run the extra Verify anyway, so you could compare platforms before running the task, to make sure there are no visible issues.

<a name="hint-4"></a>

4Hint: If you don’t care to set group writable permissions on uploaded modules, themes and any other files \*before * running any task in Aegir, you will lost write permissions to those uploaded modules, themes and uploaded files after running Clone or Migrate task. Also web server may lost write access to files, where required, which may break your site layout and any features depending on the write access to the files directory, until next morning, when all permissions will be fixed automatically. This is because Aegir creates a full backup archive (a tarball) from the site directory while moving it between platforms, and since Aegir backend runs with its own system user privileges, separate from your SSH / FTPS user, once the archive is extracted, it inherits Aegir backend user ownership, so all those files you have uploaded are no longer owned by your SSH / FTPS user. However, since both Aegir system user and your SSH / FTPS user are members of the same group, group writable permissions allow you to retain write access to all uploaded files and directories, also after running Migrate or Clone task. That is why it is of critical importance to remember about checking/setting group writable permissions, especially when you are using site specific directory space for your modules or themes. Please read more in the “Recipe #5”:http://omega8.cc/the-best-recipes-for-disaster-139#fail-e.