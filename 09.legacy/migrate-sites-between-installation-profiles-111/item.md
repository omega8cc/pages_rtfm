---
title: Migrate sites between installation profiles
slug: migrate-sites-between-installation-profiles-111
menu: Migrate sites between installation profiles
date: 21-06-2011
published: true
publish_date: 21-06-2011
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="migrate-q"></a>

QDid you know that you can easily migrate sites in Aegir also between different installation profiles, and not only between platforms using the same installation profile?

<a name="migrate-6"></a>

AThe brilliant folks at “Development Seed”:http://developmentseed.org created this awesome, hidden feature in Aegir when they decided to change the machine name of the “Open Atrium”:http://openatrium.com installation profile from ‘atrium_installer’ to ‘openatrium’. So, how to use this feature? Please take a look on how is it done in the OA “installation profile here”:http://drupalcode.org/project/openatrium.git/blob/HEAD:/openatrium.profile#l6. You can use the same trick with any other D6 profile. Say, you want to migrate the site you originally developed using Acquia installation profile where you added all required Ubercart modules to develop your online store, but now you would prefer to migrate this site to the original Ubercart platform, but the problem is, the Acquia machine name is ‘acquia’ there, while in the Ubercart platform the machine name is ‘uberdrupal’, so Aegir doesn’t show the Ubercart platform as an option to migrate the site from the Acquia platform. What to do? You only need to add one line in your uberdrupal.profile file, with ‘old_short_name’ => ‘acquia’, just below the ‘name’ => ‘UberDrupal’ line, in the function uberdrupal_profile_details(). Now remove any other not used profile directory in your target platform (also the ‘default’ profile, if exists) or Aegir will not change your site’s profile, especially if the old one exists also in the new platform. Then re-verify the Ubercart platform in Aegir and Voilà! – now you can migrate your sites from the old Acquia platform to the new Ubercart platform, and all the magic is done under the hood by Aegir!

<a name="migrate-7"></a>

ABut what if you need to migrate the site between D7 profiles? There is no hook_profile_details() there, but it is still the same easy, one-line trick. Example: your site has been created with that old Commerce Dev platform when it was using ‘commercedev’ as a machine name for its installation profile, and you want to migrate it to newer Commerce 7.x Kickstart platform, but it is using ‘commerce_kickstart’ as a machine name for its installation profile. You only need to add one line in your commerce_kickstart.info file, with “old_short_name = commercedev” (without quotes), just below “name = Commerce Kickstart” line. Then re-verify the newer Commerce Kickstart platform in Aegir and Voilà! – now you can migrate your sites from the old Commerce Dev platform to the new Commerce Kickstart platform, and all the magic is done under the hood by Aegir! And if you are on the hosted or your own Octopus instance, it is already done for you!