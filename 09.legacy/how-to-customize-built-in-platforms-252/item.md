---
title: How to customize built-in platforms?
slug: how-to-customize-built-in-platforms-252
menu: How to customize built-in platforms?
date: 27-01-2013
published: true
publish_date: 27-01-2013
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

Some built-in platforms often come with a bit outdated modules, so I would like to be able to upgrade them if there is security or feature release, and sometimes I would also like to apply a core patch, but I can’t access anything outside of the `sites/` directory.

<a name="customize-a0"></a>

»You shouldn’t assume that the platform includes some older version of some modules, even if there is a security update, only because the maintainer is too lazy to update it. Often there is some reason behind it, or even the module is patched, and by trying to override it, you could easily break all sites hosted on the same platform. See the last hint below for more information on how to test such upgrades safely.

<a name="customize-a1"></a>

»Using built-in platforms over custom platforms is recommended because their complete Drupal core along with platform root directory lives on a write protected, secure area of your hosted Aegir instance and they come with the enhanced Drupal core and all extra modules already in place, ready to use. In contrast, the custom platforms code lives in a fully writable @~/static@ directory tree, with full access to complete Drupal root directory. It is less secure, but also gives you more control over the complete codebase lifecycle and workflow.

<a name="customize-a2"></a>

»Since you can’t access anything beyond the `sites/` directory in any built-in platform, you can’t overwrite anything on the Drupal core level or installation profile level. While patching Drupal core is not possible in any of built-in platforms even on request (you really need to “built your own”:http://omega8.cc/how-to-add-custom-platform-properly-140 if you need it), you may not be aware that the core we use already has some important patches applied, like those required to properly support mixed HTTP/HTTPS sessions in Drupal 7. It also includes many other improvements, so we also encourage you to use the same core versions in “your custom platforms”:http://omega8.cc/how-to-add-custom-platform-properly-140.

<a name="customize-a3"></a>

»However, you can very easily override any contrib module or theme existing on the platform’s installation profile level, by uploading your own version of the module or theme on the `sites/all` level, which is platform specific, and then run the “Rebuild registry” task or `drush rr` on command line to make the site aware of the higher level code it should use. It works thanks to Drupal standard override order – the code uploaded in the `sites/all` space takes precedence over code in the installation profile, similarly like the code in the `sites/foo.com` site specific space takes precedence over all other lower levels.

<a name="customize-a4"></a>

»This also means that you could easily test some contrib module or theme “on a test copy of the site”:http://bit.ly/XbHmSY, just by uploading it to this site `sites/foo.com` level and running “Rebuild registry” task, without the need to create entire new (custom) Platform for quick testing. Finally, to avoid costly mistakes, you should probably read the “Aegir Basics”:http://omega8.cc/library/aegir-basics.