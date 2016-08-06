---
title: How to debug 502 Bad Gateway Error
slug: how-to-debug-502-bad-gateway-error-302
menu: How to debug 502 Bad Gateway Error
date: 07-02-2014
published: true
publish_date: 07-02-2014
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="debug-q"></a>

QWhere to start debugging when my site starts displaying Nginx \*502 Bad Gateway * or \*504 Gateway Timeout * Error on some URLs — is this a problem with the web server, the database server or the site’s code perhaps?

<a name="debug-a"></a>

AThis error is displayed by the Nginx server when it can’t communicate with the PHP-FPM backend in the expected time frame. If you see this error for more than a few seconds and on all visited URLs, including your Aegir control panel, this suggests a problem on the system side, but thanks to our monitoring we are already aware of it and working on a fix even before you submit a support request. However, it is very rare and usually the auto-healing can restart the PHP-FPM backend in a matter of seconds. While theoretically it could be also a result of some bug in the PHP version used, manifesting under certain circumstances, likely related to one of PHP extensions or even PHP core itself, in practice there are only a few main, possible reasons for this problem.

<a name="debug-1"></a>

1If the error happens immediately but randomly and you can’t see it again after reloading the same page in the browser, then it could be just a coincidence between random page visit and PHP-FPM server reload or restart. Normally this may happen only once daily, at midnight (in the server time zone), when all services are restarted during autonomous maintenance. The other possibility is that there were too many killed PHP-FPM processes due to segfaults (process crashes) caused by some buggy code in your site, so it triggered emergency PHP-FPM restart.

<a name="debug-2"></a>

2If the error happens immediately and every time you visit some page(s) only, this clearly suggests that there is some serious problem with your site’s code loaded when you visit those pages. You have to analyze what changes you have made to your site’s code or configuration before it started to happen and revert these changes, one by one, to determine what exactly crashes the PHP-FPM backend so hard. We have seen this reported by some clients after they run the upgrade to buggy release of theme in use (usually in the admin area) or after configuring duplicate and conflicting views or menu items.

<a name="debug-3"></a>

3If the error happens after waiting for the request to complete for more than 3 minutes, this simply means that your site is trying to use too much resources (usually because of waiting for some remote server to respond for too long) and hits PHP-FPM timeout limit, which closes the connection initiated by the Nginx frontend and thus everything Nginx can report is that the PHP-FPM backend “died” with the “Bad Gateway” error. In this case you need to determine which part of your site may cause this and disable it temporarily, if you will determine that the remote service it is waiting for doesn’t respond fast enough to avoid the timeout.

<a name="debug-4"></a>

4If the error happens randomly and on random URLs, this could also suggest an overloaded PHP-FMP backend which can’t provide enough workers (processes) to cope with demand from visitors. This normally never happens, unless the site is under DDoS attack and you have disabled DoS protection normally enabled for never cached URLs in the site or platform level INI file. You may need to re-enable the default protection to allow the system to stabilize and be able to serve dynamic and cached requests while refusing to hit the “naked” URLs which always hit Drupal, and thus PHP-FPM and Database backend on every request, by not logged in visitors.

<a name="debug-5"></a>

5The error may be also associated with enabled “Update Manager” module, which is a bad practice, especially when there is a large collection of contrib modules and occasionally too slow response from remote Drupal.org servers your site is trying to connect to for updates. While the “Update Manager” module is normally automatically disabled by BOA during daily maintenance, some Drupal Distributions may use dependencies which prevent us from disabling this module for you, because it would automatically disable all modules in the dependency chain. Modules and Distributions known to force the “Update Manager” module to stay enabled include: apps, agov, erpal, guardr, openacademy, openatrium, openchurch, openpublic, panopoly, restaurant.

<a name="debug-warning"></a>

!Note that typically there is very little we can do to help you with debugging this problem, because either the server error log simply registered the PHP-FPM segfault (the process crash) which happens rarely, and all we can tell is whether it is related to some PHP extension or the PHP core, or (most often) there is nothing registered in the error log, because the process crashed before it (or its parent) could catch any exception and report it.