---
# http://learn.getgrav.org/content/headers
title: Nginx redirects to /install.php with 404
slug: nginx-redirects-to-installphp-with-404-376
# menu: Nginx redirects to /install.php with 404
date: 23-03-2016
published: true
publish_date: 23-03-2016
# unpublish_date: 23-03-2016
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="debug-q"></a>

QI’ve upgraded some of our sites, first by cloning the original site and then migrating the cloned sites to the new platform. This all seemed to work fine. As a final step I’ve renamed the original site and migrated the cloned site to replace the original sites in the new platform. This worked fine on earlier releases but now I’m getting some (inconsistent) strange behavior. In some cases I get a message: 404 not found – nginx, and /install.php gets added to the domain name?

<a name="debug-a"></a>

AYou need to pay attention to aliases added to your sites, especially when you have enabled redirect to some alias and not to the main site name. Otherwise it is possible that now you have duplicate entries in different vhosts, and if one of them takes precedence because of the alphabetical order of the site name in question, it may point to non-existent path or to existing path, but without expected alias present in the aliases.php file, so Drupal assumes the site doesn’t exist and automatically forwards you to the /install.php URL, which ends up with 404 error, because BOA denies access to this file by design, for security reasons, and also because it is never used in Aegir based hosting. \*Please edit the old site’s node in Aegir to remove the alias redirect, which will remove duplicate entry from the old vhost\*. This should fix the problem.