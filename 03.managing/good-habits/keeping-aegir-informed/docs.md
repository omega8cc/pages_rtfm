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
When to Run "Verify" Before Other Aegir Tasks

Before you run certain Aegir tasks, it's a good idea to run `Verify`.
Although some tasks include `Verify` automatically, a manual `Verify`
lets you troubleshoot problems before trying to run a complex task.

Task: Verify Before Other Aegir Tasks
-------------------------------------

-   If you have copied any modules, themes, or libraries into this
    platform within the last 24 hours, you may need to
    [set correct permissions](file-dir-perms) and run `Verify` on both
    this platform
    and each of its sites. Make sure to `Verify` before running any
    other Aegir tasks.

-   Before running `Clone`, run `Verify` on the site and its platform.

-   After running `Clone`, run `Verify` on both the original and the
    cloned sites.

-   Before running `Migrate`, run `Verify` on the site and on both the
    current and the target platforms.

-   To [**rename a site**](rename-task), use `Migrate`, but
    **keep the site on the same platform**.
    (Never change a site's name and platform in the same
    step. This can lead to irreversible breakage.)

References
----------

[Set Correct Permissions for Files You Copy Into Aegir](file-dir-perms)

[Rename Your Aegir Site](rename-task)

[ssh]
[file-dir-perms]
[rename-task]
