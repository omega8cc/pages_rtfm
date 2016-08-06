---
title: The best recipes for disaster
slug: the-best-recipes-for-disaster-139
menu: The best recipes for disaster
date: 24-11-2013
published: true
publish_date: 24-11-2013
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="disaster-q"></a>

QCould you list, or even better, explain, all those bad things I should avoid while I’m still learning how to use Aegir system properly, so I could relax instead of turn on my panic mode?

<a name="disaster-a"></a>

AIt is probably a good idea, so we will improve this section with even more “recipes for disaster”, so you could enjoy reading about creative ways to destroy your sites or Aegir system instead of experience it. Note however, that our setup is pretty fear-free already, because so many dangerous things are locked to prevent problems. Yet, it is still possible for _creative_ new users to cause serious problems, even by not following best practices published in our library.

<a name="fail-a"></a>

1*How to break the site so even the Restore task will not help? * To make that happen you would need to forget about correct upgrade workflow and “good habits”:http://omega8.cc/are-there-any-specific-good-habits-to-learn-116, use Backup task in Aegir to create a pseudo-safe copy of your site, upload new contrib modules to your new platform and then use Migrate task to move/upgrade your site to the new platform. To make it even worse, you could then try to use Restore task if anything went wrong with the migration and this will either fail completely or it will revert your database, but it will leave the site in the new platform – because Restore task will never move the site back to the old platform, so all your previous backups are immediately useless, and you are locked in the new platform without any chance to rollback automatically.

<a name="fail-b"></a>

2*How to break the site and lock it in the broken state in a one step? * This sounds frightfully, but it is (unfortunately) really easy to do. All you need is to skip the steps with creating and testing the site’s clone in the existing platform first and simply use the Clone task to clone the site directly to the new platform. While this appears to be a handy shortcut, it is in fact one of the best recipes for disaster. Why? Because Aegir will not be able to properly check for all possible issues related to the contrib code and db updates to alert you before running the Clone+Migrate task. Yes, this kind of Clone task is in fact Clone and Migrate in a one step. It is very handy, but only when you already tested it with both old and new platform before. To stay safe, just avoid cloning the site to the different platform directly. Instead, clone it first in the existing platform, then migrate to the new platform, and finally re-verify it.

<a name="fail-c"></a>

3*How to create platform with no access via FTP and SSH? * Very easily if you didn’t care to really read your welcome e-mail, despite our efforts to convince you that it is a really good idea to read it. All you need is to use some makefile to create your custom platform, but specify a path to some directory outside of your “static” directory tree. All platforms available by default with your Aegir instance are installed in a separate directory tree, and their “sites” directories are symlinked in your FTP/SSH account home directory, so you don’t have an access to the root level directory in any platform. If you will use any path pointing to this tree, there will be no symlink created, hence no chance to get there via FTP/SSH. To avoid this problem always create and use subdirectories in your “static” directory tree for all your custom/extra platforms.

<a name="fail-e"></a>

4*How to get all kinds of failed migrate or clone tasks? * Very easily. Simply use sites/domain-name/modules space for your code. This will guarantee many half-broken migrations with duplicates of the same site existing in two platforms, with fatal errors because some required include file in some module no longer exists, or not yet exists, as all paths to sites/domain-name/modules change on the fly when domain-name changes, so some entries in your site’s system table will cause either failed and reverted tasks in Aegir or some nice WSOD, until you will “repair registry”:http://drupal.org/project/registry_rebuild. No, really, don’t use sites/domain-name/modules for anything and save yourself headaches and frustration. To help you understand this better, “let’s quote mig5”:http://community.aegirproject.org/node/243#comment-152 – Aegir core developer: “Aegir doesn’t track site-specific modules/themes in /sites /$yoursite /(modules|themes) because it’s not possible to ever upgrade those modules (they are tarballed up and moved with the site on a Migration). For this reason it’s unwise to store site specific modules in this directory as you’ll never be able to upgrade them if you do your upgrades properly (via Migrations, to new target platforms). To have site-specific modules not in that directory, you should learn install profiles, and store the modules/themes in /profiles /$yourprofile /(modules|themes) for a site using that install profile. (…) I don’t see us ever handling the upgrades of modules in /sites/$site, since that entire dir gets tarballed up and moved across. In fact we made a deliberate design decision to literally ignore those modules in the Aegir package system.” We highly recommend to “read all comments there(One last question re: packages)”:http://bit.ly/29bocgx. There is also “an excellent handbook entry(Migrating/upgrading and renaming websites)”:http://community.aegirproject.org/node/23 you should read to understand this better.

<a name="fail-f"></a>

5*How to guarantee that each Migrate, Clone, Restore and Backup task will fail? * Very easily. Just make sure that the @files@ directory in your site is bigger than 1GB. It doesn’t matter how many Aegir Cores you have, or if it is a Regular (SSD+SAS) or Power Core. It will always fail with the task happily “spinning forever”:https://omega8.cc/aegir-task-fails-or-spins-forever-126. As an extra bonus, it will also explode your disk and database space usage, thanks to many hidden and giant clones of the site you are trying to Clone, Migrate or Backup. Why does this happen and how to avoid this disaster? When your site’s @files@ directory is really big (1GB or more) and you have root access on your server, you should always move it and symlink properly. Aegir by default creates full, compressed archive from the @sites/foo.com@ directory on every Clone, Migrate, Restore and Backup task, so it may fail to handle this before PHP-CLI or SQL connection will time out. It is a known issue and there are plans to move @files@ directory away from @sites/foo.com@ by default and only symlink it there, but it is not implemented yet, so you need to use manual workaround for large @files@ directories and move them away, anywhere in the tree, for example to @~/static/foo_files@ and then symlink it with command @ln -s /data/disk/USER/static/foo_files /path/to/platform/sites/foo.com/files@. If you are on a hosted Aegir without root access, “contact us”:https://omega8.cc/support to have the @files@ directory symlinked, as explained above. Please remember to provide us with full system path to the site in question (type @pwd@ on command line when in the site directory to see the path we need to know).