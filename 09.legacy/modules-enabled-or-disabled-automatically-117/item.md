---
title: Modules enabled or disabled automatically
slug: modules-enabled-or-disabled-automatically-117
menu: Modules enabled or disabled automatically
date: 09-02-2015
published: true
publish_date: 09-02-2015
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="debug-q"></a>

QWhy some modules are magically enabled and other magically disabled every morning – also, is there a list of modules I should avoid?

<a name="debug-a"></a>

AThere is a (short) list of modules you should avoid because of serious performance issues caused when used: “Javascript Aggregator”:http://drupal.org/project/javascript\_aggregator and “Cookie Cache Bypass Advanced”:http://drupal.org/project/cookie\_cache\_bypass\_adv. Also, our running daily autonomous maintenance system enables some modules required to leverage all built-in performance enhancements: “Path alias cache”:http://pressflow.org (D6 only) and “RobotsTxt”:http://drupal.org/project/robotstxt (D6 and D7). It also disables a few modules, which either should never be used on any live site hosted in the high performance system or are not allowed on our servers for performance reasons: “DBlog”:http://drupal.org, “Update”:http://drupal.org, “Localization Update”:http://drupal.org/project/l10n\_update, “Poormanscron”:http://drupal.org/project/poormanscron, “Devel”:http://drupal.org/project/devel, “Ultimate Cron”:http://drupal.org/project/ultimate\_cron, “Background Process”:http://drupal.org/project/background\_process, “SuperCron”:http://drupal.org/project/supercron, “Boost crawler”:http://drupal.org/project/boost. Note that you can still enable and use both core DBlog and contrib Devel modules when needed – they are not “blacklisted”, but they will be disabled every morning (in the server timezone), because they should be used for debugging only, temporarily. To avoid this, you can use `.temporary.` or `.testing.` in the main domain name (alias is not enough) of the site during development – every such site is not affected by that procedure. Note that this procedure doesn’t touch the watchdog table, so all collected data are still available after re-enabling the DBlog again. This list can be updated with every new BOA release, so please check also: “Supported, Enabled, Disabled – a complete list”:http://omega8.cc/supported-enabled-disabled-a-complete-list-150.

 ! Note! Since “BOA-2.4.0”:https://omega8.cc/boa-240-full-edition-349 the @.dev.@ mode works only for site aliases, no longer for the main site name, so @.dev.@ keyword in the main site name will no longer exclude the site from the modules on/off procedure. We have changed this logic to avoid frequent confusion, because people tend to use @.dev.@ in the main site name and then experience various issues when going with live domain, because the site behavior changes then. To avoid further confusion we have made it so @.dev.@ mode is turned on only when it is used in the site alias, and not in the main site name. When used in the main site name, it behaves exactly as a live site domain, to make your workflow more predictable.