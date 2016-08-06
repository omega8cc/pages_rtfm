---
# http://learn.getgrav.org/content/headers
title: Your Drupal Site Upgrade &#8212; Safe Workflow
slug: your-drupal-site-upgrade-safe-workflow-298
menu: Your Drupal Site Upgrade &#8212; Safe Workflow
date: 21-07-2014
published: true
publish_date: 21-07-2014
# unpublish_date: 21-07-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

How to properly and safely upgrade a Pressflow 6 or Drupal 7 site when there is either security or feature minor version upgrade for core available? We recommend that you follow our docs and linked below articles to make the upgrade workflow safe and aware of all available Aegir features and procedures. You can find many helpful hints at:

 * “\*Managing your code in the Aegir Style\*”:http://omega8.cc/managing-your-code-in-the-aegir-style-110 (the master article to read)  
 * “\*Aegir Basics Index\*”:http://omega8.cc/library/aegir-basics-index (make sure to read all linked articles — very clearly written)  
 * “\*How to customize built-in platforms?\*”:https://omega8.cc/how-to-customize-built-in-platforms-252 (recommended if you can use built-in platforms)  
 * “\*How to add custom platform properly?\*”:http://omega8.cc/how-to-add-custom-platform-properly-140 (you don’t need it if you can use built-in platforms)  
 * “\*Git or Platforms based workflow in Aegir?\*”:http://omega8.cc/git-or-platforms-based-workflow-in-aegir-251 (some advanced overview)

There should be no issues when you follow the docs and test everything on the cloned copy of your site first. After reading all recommended docs you will see that the standard procedure typically involves the steps outlined below. Note that in the step #2 below you could upload exactly the same contrib modules you have on the old platform if you intend to upgrade Drupal core only. We even recommend to split core and contrib upgrades, to make them maintainable. Of course \*if you maintain your codebase with the help of makefile and you are using custom platforms, you should skip steps 2, 6, 9 and 10 * below.

\# \*Create a “new”:https://omega8.cc/how-to-add-custom-platform-properly-140 platform * (or use some “pre-built”:https://omega8.cc/how-to-customize-built-in-platforms-252 platform if available and applicable)  
 # \*Copy the same * (not new!) \*contrib modules into new platform and Verify it *  
 # \*Clone your live site to * @upc.foo.com@ \*in the existing, old platform *  
 # \*Migrate * @upc.foo.com@ \*to the new platform and make sure it works fine *  
 # \*Enable update module * (in the \_new\_ platform) with `'drush @upc.foo.com en update -y'`  
 # \*Upgrade contrib modules * (in the \_new\_ platform) with `'drush @upc.foo.com up --no-core'`  
 # \*Test * everything in the upgraded @upc.foo.com@ site to make sure it works fine  
 # \*Clone your live site to * @old.foo.com@ \*in the old platform * for recovery purposes  
 # \*Clone your live site to * @new.foo.com@ \*in the old platform * for final test  
 # \*Migrate * your @new.foo.com@ test site to the new platform and test how it works  
 # \*Migrate * your @foo.com@ live site to the new platform and make sure it works fine

<a name="workflow-note-a"></a>

!You could think that you could skip some steps and simply migrate the live site to the new platform after checking that its cloned copy survived the upgrade and works fine. But what if something will not work this time and Aegir built-in rollback procedure will not be able to move the site back to its old platform without errors? You could lock yourself using such shortcut in situation where the live site is no longer available on the old platform, and there are too hard to debug and fix issues on the new platform, despite prior testing. That is why we recommend these extra steps, so if things will go wrong anyway, you will always be able to recover manually, by “deleting the node of the failed live site in Aegir”:https://omega8.cc/aegir-task-fails-or-spins-forever-126 first, so it doesn’t block the Rename task, and simply Rename @old.foo.com@ to @foo.com@ in the old platform to get it back online.

<a name="workflow-q"></a>

QWhat if some contrib module of the same version in both platforms is reported as having lower @schema\_version@ on the new platform, thus making the new platform not available as a target for Migrate task? For example, the old platform lists the @file\_entity@ module as @7.x-1.3 (7215)@ on the old platform, but @7.x-1.3 (7100)@ on the new platform?

<a name="workflow-a"></a>

AThis may happen when you have a module you have tested with in-place code upgrade (so ignoring the most fundamental Aegir, and Drupal upgrade in general, best practice) or when you have the same dev version of the module in both platforms, but the module in the new target platform has lower @schema\_version@ set in its @foo.install@ file, in the last @foo\_update\_SERIAL@ function, because, for example, the same module in the old platform has some patches applied, which addeded also some db updates, thus increasing the value of @schema\_version@. If these numbers are the same in the @foo.install@ module’s file in both platforms, then the problem is caused by incorrect @schema\_version@ value in the site’s @system@ table. This happens when you have downgraded the module in-place without uninstalling it, so the record in the @system@ table still references some newer @schema\_version@ and this will make Aegir think that you are attempting to migrate the site to platform with older code, effectively attempting downgrade, which is obviously not supported and this situation will make the new platform not available (listed as an inactive option in the Migrate dialog window). You should check twice what is the real, correct @schema\_version@ listed in the module @foo.install@ file (on the old platform where the site exists) as @SERIAL@ in the last @foo\_update\_SERIAL@ function and edit respective record in your site’s database @system@ table using Chive Manager (you can find a link to Chive in your long welcome e-mail). Then you should re-Verify the site and its current platform in Aegir, and only then you can check again if the new platform is available as a target for the Migrate task, and if there are no other errors reported in the Migrate dialog window when you click on the “Compare platforms” link.

<a name="workflow-note-c"></a>

!Do not confuse this how-to with major (like D6->D7) core upgrade, though, which is not discussed here, because it is usually much more complex, thanks to Drupal core which doesn’t care to provide some really working upgrade path, so starting with D8 it will even recommend to use (hopefully) “built-in import procedure”:https://groups.drupal.org/imp instead of (impossible) migrate path.