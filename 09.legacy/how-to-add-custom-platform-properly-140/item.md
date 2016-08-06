---
title: How to add custom platform properly?
slug: how-to-add-custom-platform-properly-140
menu: How to add custom platform properly?
date: 19-05-2015
published: true
publish_date: 19-05-2015
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

How to add your custom platform so it will work like all other platforms installed by default? Is there recommended workflow, directory location, structure, or any other BOA specific details to follow?

<a name="custom-d"></a>

!Note: if you prefer to build new codebase for Aegir platform using Drush Make, you may need to clean up your environment before running the build with two commands: @’drush cc drush’@ and @’rm -rf ~/.tmp/*’@. Otherwise any broken build may generate never deleted properly leftovers, which will break subsequent builds. Note that @~/.tmp/*@ is purged for you daily, but the cleanup agent will delete only files which are older than created 24 hours ago, to not break any running build.

<a name="custom-a"></a>

»As explained in your welcome e-mail, you should use the @~/static@ directory to host your custom platforms. You can create them by traditional upload via FTP, SFTP or rsync over SSH, on command line with @’drush make my-makefile ~/static/foo-bar’@ or with makefile (local or remote) via your Aegir control panel. We highly recommend to use the command line method, to avoid issues with permissions and to make debugging easier without adding ghost platforms nodes in Aegir for failed builds (this may happen if your makefile requires newer Drush Make version) — just add @’-d’@ flag at the end of drush make command.

<a name="custom-a"></a>

»Now, the only thing you should remember about (but only when you run drush make on command line or you have downloaded your platform codebase with wget, curl or git) is to set group writable permissions: @’chmod -R 775 ~/static/foo-bar’@. You must set this chmod *before * adding the platform in the Aegir interface, or it will yell with errors or cause warnings later. Please make sure you have read the inline help in your Aegir control panel at /node /add /platform, to not confuse “Platform Path” with “Platform Makefile”.

<a name="hint-3"></a>

»Hint: You can see some (yellow) warnings about permissions when you run tasks in Aegir on the newly created platform, like “chmod to 2775 failed” or “chmod to 751 failed” for @/sites@, @sites/all@, @sites/all/modules@ etc. These tasks didn’t fail. The warnings you see are not errors, and are safe to ignore. These not harmful warnings were always logged in custom platforms, just unnoticed, because previously Aegir didn’t mark any task with that yellow icon if there were any warnings in the task log, but now it does. These directories are expected to be owned by Aegir system user and not your FTP/SSH user nor restricted only for the web server user, hence the warning, but the system will fix the ownership and permissions there every morning.

<a name="custom-a"></a>

»You should also read: “Extra modules available in all platforms”:http://omega8.cc/extra-modules-available-in-all-platforms-123, “Supported, Enabled, Disabled – a complete list”:http://omega8.cc/supported-enabled-disabled-a-complete-list-150 and “Modules enabled or disabled automatically”:http://omega8.cc/modules-enabled-or-disabled-automatically-117.

<a name="custom-b"></a>

»For Drupal 7 based custom platforms (when default profiles are used) we recommend to rename too generic profiles names – from “Standard” to “Vanilla Standard” and from “Minimal” to “Vanilla Minimal” in their corresponding .info files, to match BOA naming convention used for built-in platforms. In the file: @standard.info@ it should be “name = Vanilla Standard”. In the file: @minimal.info@ it should be “name = Vanilla Minimal”. We recommend to remove the @testing@ profile, unless it is used. Then re-verify the platform. Note that for any platform with custom profile it is best to remove all other not used default profiles.

<a name="custom-c"></a>

!We highly recommend that when building your custom platforms, you use the same enhanced Drupal core we use in all built-in platforms. You can easily download latest “Drupal 7”:http://files.aegir.cc/core/drupal-7.44.1.tar.gz and “Pressflow 6”:http://files.aegir.cc/core/pressflow-6.38.2.tar.gz exported from repositories maintained on “GitHub”:https://github.com/omega8cc. Here is an example on how to properly reference our latest available Drupal core versions in your makefiles:

@; For Drupal 7:@  
 @projects[drupal][type] = “core”@  
 @projects[drupal][download][type] = “get”@  
 @projects[drupal][download][url] = “http://files.aegir.cc/core/drupal-7.44.1.tar.gz”@

@; For Drupal 6:@  
 @projects[pressflow][type] = “core”@  
 @projects[pressflow][download][type] = “get”@  
 @projects[pressflow][download][url] = “http://files.aegir.cc/core/pressflow-6.38.2.tar.gz”@

<a name="custom-e"></a>

!If you plan to use makefile referencing private repo(s), you need to create SSH key on your account first, typically with command @’ssh-keygen -b 4096 -t rsa -N “” -f ~/.ssh/id_rsa’@ and upload the @~/.ssh/id_rsa.pub@ file to your private Git repo account at github.com, codebasehq.com or bitbucket.org, etc. But if you prefer to use Aegir interface for makefiles, so the Aegir system user will build the platform codebase for you (after you have verified that this makefile works fine on command line) and that makefile references private repos, you need to upload the public SSH key of your Aegir system user instead – it is available in your account as @~/static/USER.id_rsa.pub@ where @USER@ is a placeholder for your Aegir system username.