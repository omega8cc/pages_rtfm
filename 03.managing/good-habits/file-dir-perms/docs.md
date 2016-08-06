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
Set Correct Permissions for Files You Copy Into Aegir

When you copy files or directories into Aegir, Aegir will *usually*\
set the correct permissions. However, to avoid headaches, you should\
understand when and how to set correct permissions manually.

Task: Set Correct Permissions For Files You Copy
------------------------------------------------

These steps will set all possible permissions for your site.

1.  [`ssh` in](ftp-ssh-access) to your Aegir account

<!-- -->

1.  `cd` to the site-specific directory for your Aegir site. If your\
    site is `foo.com`, this will be `sites/foo.com/` in the
    [platform](platform)\
    directory.

<!-- -->

1.  `chmod -R 775 libraries/* modules/* themes/*`

<!-- -->

1.  `chmod -R 777 files/*`

**** Use **777** here, not **775**

**** Ignore any "Operation not permitted" warnings.

1.  `cd` into `sites/all`.

<!-- -->

1.  `chmod -R 775 libraries/* modules/* themes/*`

<!-- -->

1.  Now run the `Verify` task on every [platform](platform)\
    and site affected by these new files and directories.

More Information
----------------

### When Do You Need to Set Permissions Manually?

Aegir **will** set correct permissions automatically when you upload\
files or directories using **SFTP** or **FTPS**.

The exception are files in `sites/foo.com/files/`. If you **overwrite**\
a file that needs to be writable by the web server, you can cause\
problems, such as a broken layout.

Aegir **will not** set correct permissions when:

-   files have been transferred via `rsync` or `scp` on the command line
-   files have been downloaded with `drush` on the command line
-   files have been extracted from `tar` or `zip` archives on the
    command line

Every morning (in the local timezone for your server/datacenter), a\
[BOA](boa) maintenance script will automatically fix all these\
permissions.

However, if you run Aegir tasks while the permissions are still
incorrect,\
you can cause problems. You should fix permissions\
manually **before you run any Aegir tasks**.

### What If You Don't Set These Permissions?

-   You can **lose write permissions** to your uploaded files if you
    run\
    the `Clone` or `Migrate` task.

<!-- -->

-   The **web server may lose write permissions**, which can break your\
    site layout. Many site layouts require the web server to write\
    temporary files to the `files/` directory.

These issues will not resolve until the maintenance script runs in the\
morning.

### Must You Set Permissions After Updates?

**Yes**. When you download updated libraries, modules, or themes, these\
are new files. You must set correct permissions, just as you did with\
the original files.

### Which Directories Cannot Be Changed?

Never try to `chmod` the `files/`, `modules/`, `themes/` or\
`libraries/` directories themselves. Instead, `chmod` their\
subdirectories and files, by adding the `-R` switch and an asterisk
(`*`).

This command will **fail**:

`chmod 777 files/`

But this command is **correct**:

`chmod 777 -R files/*`

### "Operation Not Permitted"?

If you `ssh` in and set correct permissions within the `files/`\
directory, you may see this error: `Operation not permitted.` This is\
expected, because your SSH user is neither an owner of this directory\
nor of any files owned or created by the web server.

But this error can safely be ignored. The command will still set\
correct permissions for any files you have uploaded.

References
----------

[Keeping Aegir Informed With Aegir Tasks](keeping-aegir-informed)

\[ftp-ssh-access\]\
\[platform\]\
\[sites-all-modules\]\
\[keeping-aegir-informed\]
