---
# http://learn.getgrav.org/content/headers
title: Import your sites to Aegir in 8 easy steps
slug: import-your-sites-to-aegir-in-8-easy-steps-109
menu: Import your sites to Aegir in 8 easy steps
date: 22-01-2013
published: true
publish_date: 22-01-2013
# unpublish_date: 22-01-2013
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

This is our standard recipe, useful when you need to import a site with some older Drupal core or some custom installation profile (please see Hint #7 for custom profiles). When it is a site already running on the latest Drupal core (Pressflow or vanilla Drupal), available also as a default platform in your Aegir instance, there is no need to import it as a platform – instead start with step #4 and then remember only to set correct permissions on the files uploaded to the newly created site, as explained in step #2. Of course you still need to upload any modules and themes you had in the sites/all platform level.

<a name="hint-sites"></a>

!Note: if you are importing some existing multisite setup, you should create an empty platform without any sites first. There should be no site uploaded inside the `sites/` directory tree when you are adding the platform in Aegir, because otherwise Aegir will discover those sites and will try to import them, and it will fail, because their databases don’t exist yet. If something like this will happen, “delete the platform node in Aegir”:https://omega8.cc/aegir-task-fails-or-spins-forever-126 (it will delete all failed sites nodes), move away all sites from the `sites/` directory and proceed with correct workflow, as explained below. “More info”:https://omega8.cc/import-your-sites-to-aegir-in-8-easy-steps-109#hint-2.

<a name="hint-pressflow"></a>

!Note: Pressflow core is required for all D6 and D5 sites, but at the same time it is also expected that imported site (and its platform) can be initially based on vanilla Drupal and not Pressflow. We even recommend to start with 1:1 copy of your previous environment and then either use one of built-in Pressflow based platforms or “create your own platform”:https://omega8.cc/how-to-add-custom-platform-properly-140 with Pressflow core and “migrate your imported site”:https://omega8.cc/library/aegir-basics there.

<a name="hint-pressflow-required"></a>

!Note: you can use vanilla D6 or D5 based platform only during the intermediate post-import phase, just to make sure that the initial import will not be affected by any on-the-fly code changes, but you can’t use non-Pressflow core on any live site. You must migrate to Pressflow based platform as soon as possible, and before pointing your DNS to your hosted Aegir instance IP address, because running vanilla Drupal 6 or Drupal 5 based sites is not allowed and breaks our “Acceptable Use Policy”:https://omega8.cc/aup.

1Upload or rsync full drupal root of your site to the @~/static/my@ directory. It is an example path only – it can be anything inside the @~/static@ directory tree.

2Chmod everything with command: @chmod -R 775 ~/static/my@ and files only with command: @chmod -R 777 ~/static/my/sites/drupal/files/\*@

3Add platform in Aegir using full system path, so it will be (in this example where we use placeholders) @/data/disk/USER/static/my@

4Create a new, blank site in the new platform with your final domain like foo.com – don’t use any other temporary (sub)domain in this step – see “Hint #8 below”:https://omega8.cc/import-your-sites-to-aegir-in-8-easy-steps-109#hint-8.

5Copy all files from @sites/drupal/files@ to @sites/foo.com/files@ with command: @cp -af sites/drupal/files/ * sites/foo.com/files/@ – see “Hint #3 below”:https://omega8.cc/import-your-sites-to-aegir-in-8-easy-steps-109#hint-3.

6Import your database via Chive or with command @drush @foo.com sqlc

7Rename the site (using Migrate task) twice – first to some temporary subdomain like bar.foo.com and then back to your final domain foo.com – see “Hint #8 below”:https://omega8.cc/import-your-sites-to-aegir-in-8-easy-steps-109#hint-8.

8Finally, re-verify the site in Aegir. Now all paths to images should be properly rewritten both in the ‘files’ table and in the ‘node\_revision’ table. Done!

<a name="hint-1"></a>

1Hint: Replace @USER@ with your Aegir Octopus system (not SSH/FTP) username. Your Aegir system username is the same as your FTP/SSH username, minus @.ftp@, so if your FTP/SSH username is @12345678.ftp@ then your Aegir system username is @12345678@. NOTE: you don’t have an access to your Aegir system user, it is mentioned here only to help you using correct path.

<a name="hint-2"></a>

2Hint: If your site has been installed as a Drupal multisite on your previous server, so not in the @sites/drupal@, then you have to upload its files and optionally themes and modules existing in the @sites/foo.com@ \*after * you created an empty site in the step #4 above. Please don’t upload @sites/foo.com@ directory in step #1 – you need to upload it in the step #5 and then fix permissions with command: @chmod -R 777 ~/static/my/sites/foo.com/files/\*@

<a name="hint-3"></a>

3Hint: You may see some warnings like “Operation not permitted” when running recursive @chmod@ command on the @files@ directory. This is expected, because your FTPS/SSH user is not an owner of this directory and files owned/created by the web server, yet, you still can (and should) change permissions as recommended in our how-to above, because it will set correct permissions on files uploaded by you. You can also see some (yellow) warnings about permissions when you run tasks in Aegir on the imported site, like “chmod to 2775 failed” or “chmod to 751 failed” for @/sites@, @sites/all@, @sites/all/modules@ etc. These tasks didn’t fail. The warnings you see are not errors, and are safe to ignore. These not harmful warnings were always logged in custom platforms, just unnoticed, because previously Aegir didn’t mark any task with that yellow icon if there were any warnings in the task log, but now it does. These directories are expected to be owned by Aegir system user and not your FTP/SSH user nor restricted only for the web server user, hence the warning, but the system will fix the ownership and permissions there every morning.

<a name="hint-4"></a>

4Hint: If you are importing site developed in your local environment with name like ‘domain.local’, it is possible that some modules will expect ‘domain.local’ in the include path for some included files, and it will cause fatal errors if the path doesn’t exist on the server where you are importing the site and its database. The solution is to create the site with name used in your local environment – like ‘domain.local’ – in step #4 initially, and rename it to its real domain in step #7.

<a name="hint-5"></a>

5Hint: Make sure you don’t have prefixes for your tables in your database dump file before importing it, since Aegir doesn’t support db prefixes and/or tables shared between sites. Simply replace any ‘prefix\_tablename’ with ‘tablename’ in the database dump file. Also remember that it must include the DROP lines, like ‘DROP TABLE IF EXISTS `access`;’ etc. but it shouldn’t attempt to create new database. We recommend that you prepare the database dump before importing it, with special tool we provide: `sqlmagic fix file.sql` and then import fixed dump, which has prefix added to its filename: `fixed-file.sql`

<a name="hint-6"></a>

6Hint: When your site’s files directory is big (1GB or more) and you have root access on your server, always symlink large files directory. Aegir by default creates full, compressed archive from the @sites/foo.com@ directory on every Clone, Migrate, and of course Backup task, so it will fail on servers without enough RAM and CPU power to handle this before PHP-CLI or SQL connection will time out. It is a known issue and there are plans to move @files@ directory away from @sites/foo.com@ by default and only symlink it there, but it is not implemented yet, so you need to use manual workaround for large @files@ directories and move them away, anywhere in the tree, for example to @~/static/foo\_files@ and then symlink it with command @ln -s /data/disk/USER/static/foo\_files /path/to/platform/sites/foo.com/files@. If you are on the hosted Aegir without root access, “contact us”:https://omega8.cc/support to have the @files@ directory symlinked, as explained above.

<a name="hint-7"></a>

7Hint: When your imported site is based on some custom installation profile not available in platforms installed by default, plus it is a vanilla Drupal core and not Pressflow, then you will be interested in our “recipe for migrating the site between installation profiles”:https://omega8.cc/migrate-sites-between-installation-profiles-easily-111. Note however, that you can use this recipe easily only when you have full access to your Aegir system – which is possible when it is hosted on your own server. Otherwise you need to simply replace the Drupal vanilla core with corresponding Pressflow version in the step #1 above. Another option would be to create another custom, but Pressflow based platform, so you could use the “recipe for migrating the site between installation profiles”:https://omega8.cc/migrate-sites-between-installation-profiles-easily-111 even if you are using managed Aegir hosting.

<a name="hint-8"></a>

8Hint: You should create a blank site in the step #4 using your final, live domain name and then rename the site twice in step #7 to get all paths to files rewritten properly. These steps, in this exact order, are required to allow Aegir to replace all paths like @sites/drupal/files@ with @sites/foo.com/files@ – both in the files table and even in your content, just in case they are hardcoded there after using wysiwyg editor etc. This magic automates otherwise tedious and frustrating manual replacements in the database and in the content. Still, there are places where hardcoded @sites/drupal/files@ path can’t be replaced with proper, Drupal multisite compatible paths, like in your custom themes settings, so you may still need to fix some of them manually.