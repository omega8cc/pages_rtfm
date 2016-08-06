---
title: TITLE
slug: URI
menu: MENU
date: 08-08-2016
published: true
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /URI
---
Where Is the Rename Task?

The Aegir admin panel offers a list of possible tasks, but there is no\
`Rename` task.

Task: Rename Your Site's Main Domain
------------------------------------

To "rename" your site to a new main domain, **use the `Migrate` task**.

Do **not** change the platform. Instead, leave the platform unchanged,\
and simply enter the new domain for your site.

More Information
----------------

### Never Change the Domain and the Platform in One Step

The `Migrate` tasks triggers many steps behind the scenes, so it is\
critical never to change both the domain name and the platform in one\
step. Doing so could make it impossible to run the `Backup` task and\
undo any mistakes.

If you're renaming the domain, keep the site on the same platform.

If you're migrating to a new platform, keep the same domain name.

### "www." Prefix Requires Special Handling

If you want to add or remove the "www." prefix from your domain name,
you will\
need an extra step.

First, `Migrate` the site to some other domain, like `anything.foo.com`.

Then, `Migrate` from `anything.foo.com` to `www.foo.com` or `foo.com`.

The reason for the extra step is that Aegir automatically creates an\
*alias* based on the main domain. The domain `foo.com` gets an alias\
of `www.foo.com`, and the domain of `www.foo.com gets an alias of
`foo.com@. You can't change a main domain to one of its aliases\
directly.

### References

[How to Manage Aliases and Redirects](manage-aliases-redirects)

\[manage-aliases-redirects\]
