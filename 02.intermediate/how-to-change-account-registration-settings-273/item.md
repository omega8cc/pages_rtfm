---
# http://learn.getgrav.org/content/headers
title: How to change account registration settings?
slug: how-to-change-account-registration-settings-273
# menu: How to change account registration settings?
date: 01-06-2013
published: true
publish_date: 01-06-2013
# unpublish_date: 01-06-2013
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

<a name="registration-q"></a>

QHow to change account registration settings in any of hosted sites, so these settings will not revert back to hardcoded, secure defaults, and how to automate this procedure?

<a name="registration-a"></a>

ARegistration settings are now restricted by design to protect your sites from unintended turning them into spam machines (which is allowed by Drupal 6 default settings, sadly). Spambots targeting Drupal sites are already a plague, so \_unless you have already set more strict permissions “Administrators only”\_, we force reasonable default policy for new accounts registration: “Visitors, but administrator approval is required” plus “Require e-mail verification when a visitor creates an account” enabled. If you wish to disable e-mail verification or set “Who can register accounts” to “Visitors”, you must set `disable_user_register_protection = TRUE` in the site level “INI file”:https://omega8.cc/how-to-control-boa-on-site-and-platform-level-293. Now you will be able to permanently change these settings in the foo.com site. Without this variable set to TRUE in your site’s INI file, our default protection will be enabled again the next day (early morning in the server time zone). Note that we don’t force “Administrators only”, because it could immediately break many commerce or community sites essential features. But for other sites, “Administrators only” is strongly suggested. Note that this is a \_site specific\_ only and not a platform wide setting and control file.

<a name="registration-b"></a>

!You can optionally enforce “Administrators only” mode for all sites in the platform by setting `enable_user_register_protection = TRUE` in the platform level “INI file”:https://omega8.cc/how-to-control-boa-on-site-and-platform-level-293. Note that it will not override the site specific INI file, so any site on the same platform can still use individual settings. It is even possible to automate this, so our running daily (early morning in the server time zone) maintenance system will create the platform level control files in all your platforms with active sites. You only need to create a single, central control file @enable\_user\_register\_protection.info@ in the @~/static/control/@ directory in your account. Note that this is a \_platform wide\_ and not a site specific setting and control file.

<a name="registration-c"></a>

!Note that both “INI settings”:https://omega8.cc/how-to-control-boa-on-site-and-platform-level-293 affect only the maintenance system (which runs daily) behaviour — they don’t affect the site behaviour directly in a live mode, as it was before, so you can modify the settings in the site admin, and they can be overridden, depending on the variables defined in “INI files”:https://omega8.cc/how-to-control-boa-on-site-and-platform-level-293, as explained above, when the maintenance system runs again.

<a name="registration-d"></a>

!Please be aware that if you change “Who can register accounts” to “Visitors” because your site requires open registration, you are fully responsible for your site security and you should use well configured anti-spam modules and monitor your site users activity to make sure that spambots can’t create accounts and any such accounts are quickly deleted to avoid turning your site into spam machine and/or self-DoS engine.

<a name="explanation"></a>

!This change has been introduced in an emergency mode, so without waiting for a new BOA system release, because many of our servers suffered from sudden and random load spikes for a few weeks, and we have determined that it was because of some widespread spambots attacks we have never seen before on that scale, affecting sites with too open new accounts registration policy. We have tried to fight this for a few weeks, hunting for sites targeted and improperly configured, but it was not effective enough, so to protect all our clients who do care about security and proper configuration, from being indirectly affected by this new wave of spambots attacks emerged, we have decided to force settings, which introduce protection for unprotected sites, but also don’t break possibility to self-register, when required, and introduce a one-time inconvenience as a price for a long-term protection from systems instability. We are sorry for any inconvenience caused. We strongly recommend to check if your sites are not already “taken over” by spambots – we have seen too many sites with 10k or even 50k spambots accounts created, not to mention \_tons of spam\_ added, which even if not published, can slow down your site seriously anyway.

<a name="registration-e"></a>

!Please understand that by removing this default protection, you are making all sites hosted on your instance vulnerable to potential DoS attacks, which are very common these days, with networks of spambots targeting Drupal sites with attempts to add spam as nodes, comments and registering new accounts. We reserve the right to restore default protection if our monitoring will detect that removed restrictions allowed to successfully attack your site and cause system instability.