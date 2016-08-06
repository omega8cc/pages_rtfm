---
title: How to use New Relic Apps Monitoring?
slug: how-to-use-new-relic-apps-monitoring-335
menu: How to use New Relic Apps Monitoring?
date: 20-09-2014
published: true
publish_date: 20-09-2014
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

Starting with BOA-2.3.1 you can very easily enable New Relic Apps Monitoring with per Octopus instance license key. It will work for all sites on the same instance, and every site will get its own Application profile automatically created in your New Relic control panel, to make monitoring and debugging super-easy.

To initialize your account properly to support  “New Relic Apps Monitoring”:http://newrelic.com/application-monitoring,  add your license key in the special control file @~/static/control/newrelic.info@ and wait a few minutes before you will notice first sites listed as separate Applications in your New Relic control panel. Please note that valid license key is a 40-character hexadecimal string that New Relic provides when you sign up for an account.

<a name="newrelic-red"></a>

!This new feature will disable global New Relic monitoring by deactivating server-level license key, so it can safely auto-enable or auto-disable it every 5 minutes, but per Octopus instance — for all sites hosted on the given instance — when a valid license key is present in the instance specific control file. It will also disable newrelic-sysmond service, if running.

Please note that on a self-hosted BOA you still need to add your valid license key as @_NEWRELIC_KEY@ in the @/root/.barracuda.cnf@ file and run system upgrade with @’barracuda up-stable’@ first. This step is not equired on Omega8.cc hosted service, where New Relic agent is already pre-installed for you.

To disable New Relic monitoring for the Octopus instance, simply delete its @newrelic.info@ control file and wait a few minutes.