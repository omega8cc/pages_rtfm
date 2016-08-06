---
title: How to use Chive Manager?
slug: how-to-use-chive-manager-323
menu: How to use Chive Manager?
date: 10-07-2014
published: true
publish_date: 10-07-2014
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

You can manage your databases via Chive Manager web interface, using access credentials (dbhost, dbname and dbpass) available in every site’s @drushrc.php@ file, located in the same directory as your site’s @settings.php@ and @local.settings.php@ files. However, you need to authenticate your IP address by opening active SSH session, before the access to Chive will be granted on the fly. Otherwise you will see just Nginx 403 error when visiting URL listed in your welcome e-mail.

If you are not familiar with SSH, “here is a quick intro on using SSH with Mac Terminal”:http://www.youtube.com/watch?v=J\_8ZsXP1EYk. Similar terminal apps are available for all operating systems, for example “PuTTY SSH for Windows”:http://www.putty.org. When you have your terminal window open, type this command and hit Enter on your keyboard: `'ssh USER@HOST'`. Of course replace @USER@ and @HOST@ placeholders with your account credentials listed in the section #3. Adding Modules & Themes in your welcome e-mail. It will ask you to accept SSH key and then it will ask for your account password.

Once logged in your account, type this command and hit Enter on your keyboard: `'ping -i 30 google.com'`. It will run automatically every 30 seconds until you will log out or simply close the Terminal window. For as long as this command is run automatically, the system will grant you the access to the Chive Manager via the URL you can find in the section #4. Managing Your Databases in your welcome e-mail.

!Don’t confuse SSH credentials with your Aegir control panel credentials. The system will update access rules every 10 seconds, so please wait a moment before visiting Chive URL again.

»Why is this special protection important? While BOA forces HTTPS connection for Chive, anyone who knows the URL can access it and attempt to either run brute-force attack to get into your site’s database, or at least attempt to hammer the server and cause DoS-like effects, at least until the system will block his IP on the firewall. The other important reason is that your site’s DB credentials change only when you migrate or rename the site, and otherwise remain intact. Now, what if you have an employee or a freelancer whom you no longer want to be able to access your site? If you think that deleting his SFTP sub-account is enough, think again. He still can access your site’s database via Chive, if he knows the site’s DB credentials and the Chive URL. But now it’s no longer possible. Only the visitor who is able to successfully authenticate himself via SSH, and keeps active SSH session, will be able to access the Chive URL. The rest of the world will see just dummy Nginx 403 Access Denied error.

 You can also use any desktop SQL manager you prefer, if it supports tunneling over standard SSH port 22, since there is no remote access over mysql port 3306 available, for security and performance reasons – “see this video tutorial for details”:http://bit.ly/om8rsql.

You can also manage your databases on command line, either with supported Drush commands or directly with tools like @mysql@ and @mysqldump@.  For Drush basic tips, please check also “How to use Drush aliases”:https://omega8.cc/how-to-use-drush-aliases-321.